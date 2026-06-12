---
title: "HOWTO: Set Up the Nintendo Wi-Fi USB Connector In the Latest Build of Ubuntu"
date: 2008-07-31
forum: Hardware
---

### Post by Unanimated on 2008-07-31
**This thread is regarding Ubuntu 8.04.1 kernel 2.6.24-19, and possibly any later build.**

Now, I know there is a thread already regarding this, but one of the instructions that the he offers might be causing people some frustration. It happens when you make the group usbfs. After you unlock the Users and Groups menu, open Manage Groups, and click Add Group. Make the name usbfs, add all the users who might need it, blah blah. The number that is UNDER usbfs is EXTREMELY important. Later in the guide, when he tells you to put in:
# **85** is the USB group
none /proc/bus/usb usbfs devgid=**85**,devmode=664 0 0

You should change the numbers in bold to the number that was under the word usbfs.

Oh yeah--I'm talking about this guide:
[http://ubuntuforums.org/showthread.php?t=640083]("http://ubuntuforums.org/showthread.php?t=640083")
Hope this might help you in the switch from Windoze to Ubuntu!
[Sorry if this guide is unnecessary.]

---

