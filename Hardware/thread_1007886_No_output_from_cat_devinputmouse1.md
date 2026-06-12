---
title: "No output from cat /dev/input/mouse1"
date: 2008-12-10
forum: Hardware
---

### Post by renegade007 on 2008-12-10
Hi,

I`m writing a program to read data from a USB mouse.

In order to do that, I need to specify the correct device path for the mouse.

Now although my mouse is working fine and i get the correct mouse movement,
I am not getting any output from "cat /device/input/mouse1" on the console
when i move the mouse around. (I am doing this so that i know i am using the correct
device path)

I know that mouse1 is the correct node as when I plug in the mouse and remove it,
"mouse1" appears and disappers respectively from /dev/input/ . Also when
I run "cat /proc/bus/input/devices", the Handler item tells me that the correct node
is mouse1.

But just in case I was wrong, I have also tried mouse0, mouse2 and mice but i stil dont get any output.

However, when I do cat /dev/input/mouse1 on my desktop PC, it does give me output but with the same mouse in my laptop, there is no output. My PC has Ubuntu 7.10 and laptop Ubuntu 8.10.

Can anyone tell me why I`m not getting any output. The mouse is working perfectly otherwise and thats whats baffling me. Also, my xorg.conf looks pretty simple. There is no "InputDevice" section there. Could this be the problem? (but the external mouse works fine)

Section "Device"
      Identifier "Configured Video Device"
EndSection

Section "Monitor"
      Identifier "Configured Monitor"
EndSection

Section "Screen"
      Identifier "Default Screen"
      Monitor "Configured Monitor"
      Device  "Configured Video Device"

EndSection


Btw, the laptop (IBM Thinkpad X200) is brand new and was just installed with Ubuntu 8.10. 

Thanks

---

