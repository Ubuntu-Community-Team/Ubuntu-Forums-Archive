---
title: "Touchpad/mouse left click has gone after upgrade to 2.6.27-9"
date: 2008-12-06
forum: Hardware
---

### Post by erop on 2008-12-06
Hello, everybody!
Here is a description of my small problem which solving took already more then week and a couple of silver hairs :)

After a new kernel 2.6.27-9 was released I noticed a usual red arrow in the Panel. Double click, Update Manager started, and after all update operations were finished it asked me to reboot the system. OK. But after a reboot I found that since that time I had no left click of my both Asus U5F touchpad and bluetooth mouse Logitech V470.
I rebooted the system immediately and as soon as mouse pointer appeared I started playing with it opening menu items and clicking on objects on my desktop. Firstly left click worked as usual but in about a half minute it lost again. I rebooted with previous kernel version – the same result. Then I rebooted in recovery mode of each kernel versions - left click disappeared after a half a minute or so. The second strange thing I noticed in mouse/touchpad behavior is that making double click on menu items or objects on desktop let them blinking! In other words, for the system there IS an action – left click, but there is NO reaction – opening file or menu item! Rather strange.

First of all I looked at my /etc/X11/xorg.conf  and it had no “Input device” section, only “Device”, “Monitor” and “Screen”. I started digging to HAL issues and found some advices at [https://wiki.ubuntu.com/X/Config/Input#hal](https://wiki.ubuntu.com/X/Config/Input#hal) and [http://ubuntuforums.org/showthread.php?t=965931&referrerid=718299](http://ubuntuforums.org/showthread.php?t=965931&referrerid=718299) . As written there I created /etc/hal/fdi/policy/touchpad.fdi – no positive changes. Then I copied existing /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi to /etc/hal/fdi/policy/ and remove touchpad.fdi. Left click didn't appear :( Can anybody give a proper direction for solving the problem?

Here I enclosed some files with info about my system as advised at 
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection) . Hope this help. Thank you!

---

