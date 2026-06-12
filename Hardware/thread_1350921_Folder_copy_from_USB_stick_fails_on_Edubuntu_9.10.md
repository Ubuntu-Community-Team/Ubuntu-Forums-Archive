---
title: "Folder copy from USB stick fails on Edubuntu 9.10"
date: 2009-12-09
forum: Hardware
---

### Post by svetiev on 2009-12-09
I posted this in the GENERAL HELP forum previously but I didn't get any replies, so i'm moving it here.

I have Karmic Koala installed on a Eee.PC and I downloaded the latest updates. However there is a strange problem with USB Sticks.

Whenever I try to copy a folder from or to the USB stick it fails and it seems that GRUB sort of malfunctions as well - the desktop stops responding to right mouse clicks and all the icons from it disappear (the usb stick icon and the test folder I was trying to copy).

The USB stick is still mounted though, I can find it in My Computer but now it's read only. I can still unmount and remount it again but it stays in a read only mode with the desktop not responding until a reboot.

The weird thing is this only happens when I try copying a folder. When copying single files everything works fine and there is no problem.

I'm a noob but I have some mild experience and I would greatly appreciate any kind of help.

Boris

---

### Post by svetiev on 2009-12-11
Ok i found the solution to this one. 

Because I was running a localized language support in Macedonian, Nautilus had an eror in one of it's language support files (nautiuls.mo). Someone had already fixed the faulty translation and there is a replace file that fixes the problem. Here is the file:

[http://ubuntu.linux.net.mk/forum/download/file.php?id=1&sid=178168ee5005371f8d6f01fa3c88c6d9](http://ubuntu.linux.net.mk/forum/download/file.php?id=1&sid=178168ee5005371f8d6f01fa3c88c6d9)

And this is the forum thread in Macedonian that explains why and how to fix it:

[http://ubuntu.linux.net.mk/forum/viewtopic.php?f=8&t=8](http://ubuntu.linux.net.mk/forum/viewtopic.php?f=8&t=8)

---

