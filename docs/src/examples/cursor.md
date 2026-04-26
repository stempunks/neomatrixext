# Cursor

Computers have a mouse, the Luma Matrix has a joystick. This example shows how to move a cursor on the matrix using the joystick. The cursor is represented by a yellow pixel. The cursor can be moved up, down, left, and right. When the joystick is pressed, the cursor is reset to the top left corner of the matrix.


```blocks
function moveCursor (direction: number) {
    if (direction == lumaMatrix.getJoystickDirectionEnum(lumaMatrix.eJoystickDirection.Up)) {
        cursor_y += -1
    } else if (direction == lumaMatrix.getJoystickDirectionEnum(lumaMatrix.eJoystickDirection.Down)) {
        cursor_y += 1
    } else if (direction == lumaMatrix.getJoystickDirectionEnum(lumaMatrix.eJoystickDirection.Left)) {
        cursor_x += -1
    } else if (direction == lumaMatrix.getJoystickDirectionEnum(lumaMatrix.eJoystickDirection.Right)) {
        cursor_x += 1
    } else if (direction == lumaMatrix.getJoystickDirectionEnum(lumaMatrix.eJoystickDirection.Center)) {
        cursor_x = 0
        cursor_y = 0
    } else {
        cursor_x = (cursor_x + 8) % 8
        cursor_y = (cursor_y + 8) % 8
    }
}
lumaMatrix.joystickChangedThread(function (direction) {
    lumaMatrix.setOnePixel(cursor_x, cursor_y, 0x000000)
    moveCursor(direction)
    lumaMatrix.setOnePixel(cursor_x, cursor_y, 0xffff00)
})
let cursor_y = 0
let cursor_x = 0
cursor_x = 0
cursor_y = 0
lumaMatrix.initializeMatrix(127)
lumaMatrix.setOnePixel(cursor_x, cursor_y, 0xffff00)
```

<script src="../assets/js/gh-pages-embed.js"></script><script>makeCodeRender("https://makecode.microbit.org/", "ines-hpmm/pxt-luma-matrix");</script>
