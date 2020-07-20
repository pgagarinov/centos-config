# how to use the x11vnc service
## 1. Client VNC
The application to connect to VNC must be RealVNC Viewer
## 2. Replacing the VNC password

> x11vnc --storepasswd **пароль** /etc/x11vnc.passwd 

## 3. Keyboard errors
**3.1.** To resolve problems with transmitting keyboard taps via VNC, you must:
Create a file in any convenient location (for example fix.sh) with content
> #!/bin/sh
> xmodmap -e "keycode 59 = 0x002c 0x003c 0x06c2 0x06e2"
> xmodmap -e "keycode 60 = 0x002e 0x003e 0x06c0 0x06e0"
> xmodmap -e "keycode 94 = 0x003c 0x003c 0x06c2 0x06e2"

In the start menu, write autostart in the search,
In the window that opens, click " Add script"
Select the script we created in the previous step.
Choose how to use the "Startup" script (when loading).
English should always be selected on the tail (client, home) machine, and the layout should only be changed on the remote machine.

**3.2.** There are several ways to solve problems with key sticking:

**а)** manually, in the console, if you need to enable this functionality, enter the command
> xset r on

Checking, changing the status
>xset q

**б)** in the VNC server configuration settings (you need to add the key --repeat) - this will automatically enable the keyboard "sticking" option

## 4. Мерцание экрана

You need to go to the start menu 
Find and select System Settings
Then go to the Display and Monitor section
Select Compositor in it
Select the following values:
Rendering backend == XRender
Scale method == Crisp




