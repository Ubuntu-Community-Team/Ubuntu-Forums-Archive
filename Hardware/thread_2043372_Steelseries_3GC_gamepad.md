---
title: "Steelseries 3GC gamepad"
date: 2012-08-16
forum: Hardware
---

### Post by linuxlover42 on 2012-08-16
Hi all,

I recently acquired a steelseries 3GC gamepad that I'm trying to get to work properly in linux. At first, the gamepad didn't work at all. It began to function after I installed the xserver-xorg-input-joystick driver. However, the device is now being recognized as a dragonrise joystick and the mapping is all wrong. Any help is greatly appreciated.

---

### Post by Grumbel on 2012-08-19
First of, uninstall the xserver-xorg-input-joystick, as that's for mouse emulation, not for using the gamepad in a game. 

About the miss identification of the joystick, that's normal, joystick sometimes share internals.

So next thing you should do is get jstest (apt-get install joystick) or [jstest-gtk](http://pingus.seul.org/~grumbel/jstest-gtk/). These are simply for testing and allow you to make sure that all the buttons and axis are working as expected. You use jstest from the terminal like:

$ jstest /dev/input/js0

Then just wiggle the axis and buttons around and look at the output.

When jstest works as expected, your joystick is up and running as far as Linux is concerned. Any kind of miss configuration you have to fix in the games you try to play.

---

### Post by linuxlover42 on 2012-08-24
great, thanks for the help.

---

### Post by linuxlover42 on 2012-08-24
actually, there is still a problem. the controller has two joysticks, an arrowpad, four number buttons, two triggers, and two bumpers. Currently, the left joystick and the arrowpad (also on the left) are being recognized as the same set of two axises and the right stick and number buttons (on the right) are being recognized as the same thing. also, up and down on the right stick is being recognized as a button and not an axis so I can't map the mouse to it.

---

### Post by linuxlover42 on 2012-08-24
correction, left and right on the stick are recognized as buttons instead of an axis. If I can fix that It'll all be fine.

---

### Post by perezomail on 2013-02-11
I have the 1GC steelseries and the program qjoypad works great with it .
Using the quick settup you  are using the keyboard settings in order to set it. 
try this with your controller and let me know because ive been looking on upgradeing

---

### Post by darksign13 on 2013-12-25
I don't know whether you will have allready found this out by the time you read this or not, but for the sake of others like me who find this discussion through a serch engine:

To get the controller to send out seperate signals for each of the sticks as well as the D-Pad, just hit the mode button in the center of the controller. When the green light on the left is lit, you are sending the same signals from the D-Pad and the Left stick, and the buttons and the right stick. When the red light on the right is on, however, each of the sticks send out there own unique signals. This works the same way on Linux and Windows.

---

