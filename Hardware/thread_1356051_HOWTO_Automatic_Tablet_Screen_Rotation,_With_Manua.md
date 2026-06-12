---
title: "HOWTO: Automatic Tablet Screen Rotation, With Manual Control"
date: 2009-12-15
forum: Hardware
---

### Post by roadkillbunny on 2009-12-15
I've written a python daemon that checks the orientation of a tablet pc from a built in accelerometer (currently hdaps based ones only supported), and then it rotates the screen such that it fits the physical orientation.

I think it has an advantage over some of the other scripts out there in that my daemon exposes a dbus interface that can be used to control it. For example, I wrote another script that connect to the running daemon to disable automatic rotation and switches to manual rotation. I mapped one of the buttons by the screen to it.

This is my first program that I've released, so initially it might have some problems/bad design decisions because I've only tested it on my ThinkPad X61T running Ubuntu Karmic. So I'm open to suggestions and criticism.

You can find more details about the project here: [AutoRotate]("http://www.krizka.net/projects/autorotate/")

[B]Features:
[/B][LIST]
[*] Automatic screen rotation based on the physics orientation when in tablet mode (read via hdaps module)
[*] Changing from laptop mode into tablet mode automatically rotates the screen 180 degrees, even if the tablet is in a horizontal orientation
[*] Fixes orientation of the mouse buttons and wacom stylus
[*] Minimum treshhold for change of rotation so small deviations won’t change the screen
[*] Can be controlled via dbus
[*] Control script (manual-rotate.py) that can disable automatic rotation and rotate the screen 90 degrees. Returns to automatic rotation after doing a full cycle.
[/LIST]

[B]Future Features/Plans:
[/B][LIST]
[*] GUI for controlling the daemon
[*] Support other laptops with different accelerometers
[*] Better documentation
[/LIST]

[B]Installation Instructions for Ubuntu Karmic Koala:
[/B]
[LIST=1]
[*] Make sure you have a working accelerometer that is reading the proper orientation. For ThinkPad X61T, you have to [compile the tp-smapi-source kernel module manually]("http://www.krizka.net/2009/11/01/thinkpad-x61-tablet-tilt-detection-and-ubuntu-karmic-koala/").
[*]Add my [ThinkPadX61T PPA]("https://launchpad.net/~kkrizka/+archive/thinkpad-x61t") repository by appending the following line to the end of the /etc/apt/sources.list file:
```
 deb http://ppa.launchpad.net/kkrizka/thinkpad-x61t/ubuntu karmic main
```
[*] Update apt-get’s package list:
```
 sudo apt-get update
```
[*] Install the script and necessary packages:
```
 sudo apt-get install wacom-tools python-xrandr autorotate

```
[*]To have auto-rotate.py autostart on GDM. This way it will be available to all users, even during login. This is done by adding the following line to the end of the /etc/gdm/Init/Default file before the exit 0 command:
```
 auto-rotate.py&

```
[*] Restart GDM to start the daemon:
```
 sudo /etc/init.d/gdm restart
```
[*] Swivel down your screen into the tablet mode, and tilt it at around 45 degrees to test if the script works!
[/LIST]

The following are instructions for using the control script. I should note that this script also works without a daemon running, in which case it just rotates the screen to the next rotation. With the daemon running, it disables the daemon and rotates the screen 90 degrees. After it does a full cycle, it re-enables the daemon.

[LIST=1]
[*] Open the keyboard shorcuts panel, found under System->Preferences->Keyboard Shortcuts.
[*] Click the Add button to create a new custom shortcut.
[*] In the window that pops up, specify
 *Name:* Rotate Screen
 *Command:* manual-rotate.py.
[*] Close the window by clicking Apply.
[*] Find the new shortcut at the bottom of the keyboard shortcuts of the window, and map it to a button.
[*] Close the keyboard shortcuts window, go into tablet mode and press the button that you mapped in the previous step to the manual-rotate.py script.
[/LIST]

I would also give some credit to the authors of the following scripts, because their work taught me how to accomplish certain tasks:
[list]
[*] [http://ubuntuforums.org/showthread.php?t=604896](http://ubuntuforums.org/showthread.php?t=604896)
[*] [https://help.ubuntu.com/community/X61T](https://help.ubuntu.com/community/X61T)
[/list]

---

