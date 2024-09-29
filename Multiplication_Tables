import sys
import random
from PyQt5.QtWidgets import QApplication, QWidget, QGridLayout, QLabel, QPushButton, QVBoxLayout
from PyQt5.QtCore import Qt
from PyQt5.QtGui import QColor

class MultiplicationTable(QWidget):
    def __init__(self):
        super().__init__()

        # Define the window title and size
        self.setWindowTitle("Multiplication Table")
        self.setGeometry(100, 100, 800, 600)

        # Layout for the grid
        grid_layout = QGridLayout()

        # Create labels for numbers 1 to 100
        self.labels = []
        for i in range(100):
            label_value = i + 1
            label = QLabel(str(label_value))
            label.setStyleSheet("border: 1px solid black; padding: 10px; background-color: lightblue;")
            label.setAlignment(Qt.AlignCenter)

            # Add the label to the grid layout at the correct row and column
            grid_layout.addWidget(label, i // 10, i % 10)

            # Set a mouse click event to highlight multiples when clicked
            label.mousePressEvent = lambda event, value=label_value: self.highlight_multiples(value)
            self.labels.append(label)

        # Center button to exit
        button = QPushButton("Close")
        button.clicked.connect(self.close)

        # Main layout
        main_layout = QVBoxLayout()
        main_layout.addLayout(grid_layout)
        main_layout.addWidget(button)
        self.setLayout(main_layout)

    def highlight_multiples(self, number):
        # Format the labels
        for label in self.labels:
            label.setStyleSheet("border: 1px solid black; padding: 10px; background-color: lightblue;")  # Reset the color

        # Format the highlighted label
        random_color = self.get_random_color()
        for i, label in enumerate(self.labels):
            label_value = i + 1

            # Calculate the multiples, if the label is a multiple, highlight it
            if label_value % number == 0:
                label.setStyleSheet(
                    f"border: 1px solid black; padding: 10px; background-color: {random_color};")  # Highlight in a random color

    def get_random_color(self):
        # Generate a random color in HEX format
        r = random.randint(0, 255)
        g = random.randint(0, 255)
        b = random.randint(0, 255)

        return f'#{r:02x}{g:02x}{b:02x}'  # Return hex color string


if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MultiplicationTable()
    window.show()
    sys.exit(app.exec_())
