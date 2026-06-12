---
title: "Extremely jumpy mouse cursor on Ubuntu 10.04 LTS"
date: 2010-08-14
forum: Hardware
---

### Post by nkinar on 2010-08-14
Hello,

I've recently installed Ubuntu 10.04 LTS on a Macbook Pro.  I also have a Logitech M500 wired mouse plugged into one of the USB 2.0 ports.

Both the M500 mouse and the touchpad exhibit very "jumpy" behavior.  For example, the mouse cursor may start moving even when I am not touching it.  Often the left click button will become "jammed" and it will be impossible to turn off.  This leads to much of the text being selected on a webpage.

Here is the output of my uname command:

nkinar@matilda:~$ uname -a
Linux matilda 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

What might be going on here, and how might I be able to fix this odd behavior?

---

### Post by nkinar on 2010-08-14
Perhaps this might have something to do with the touchpad?  I installed the drivers provided by the MacbookPro project following the instructions given here:

_[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Lucid)_

However, I also had to install "Pointing Devices" in the Ubuntu Software Centre to prevent some of the jumpyness.

I don't know if this is just a quick fix, or if the quirky behavior will continue.  However, the Pointing Devices package also performs hand detection to ensure that the touchpad will not interfere with the mouse.

---

### Post by nkinar on 2010-08-14
Moreover, I also found it useful on Ubuntu 10.04 LTS to go into the menus at the top of the screen and run System -> Preferences -> Mouse.  Then in the "Mouse Preferences" window, I found it beneficial to un-check "Enable mouse clicks with touchpad" under the "General" heading.

With this option enabled it appears that the Macbook Pro touchpad will initiate a click without pressing down on the button.  I suppose that such an option would be useful for touch devices without any buttons to physically press (i.e. Magic Touch/Wacom touch devices).

---

