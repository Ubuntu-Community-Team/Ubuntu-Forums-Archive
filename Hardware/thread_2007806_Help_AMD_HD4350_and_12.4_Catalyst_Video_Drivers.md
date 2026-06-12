---
title: "Help AMD HD4350 and 12.4 Catalyst Video Drivers"
date: 2012-06-21
forum: Hardware
---

### Post by raidensub on 2012-06-21
Hi. I need help. I have AMD HD4350 graphic card and i am trying to install the Catalyst Video Drivers for about 3 weeks in Kubuntu 12.04.
When i use jockey the install fails with a message to look in /var/log/jockey.log. In the package manager fglrx looks installed
and if i restart i get no desktop.

[http://pastebin.com/hQyYEcem](http://pastebin.com/hQyYEcem)

When i use a manual install using:
sudo sh amd-driver-installer-*.run --buildpkg Ubuntu/precise

it builds ok and when i install it fails and i get:

[http://pastebin.com/8RMSYhCy](http://pastebin.com/8RMSYhCy)

This is the /var/lib/dkms/fglrx/8.961/build/make.log

[http://pastebin.com/BAJqykya](http://pastebin.com/BAJqykya)

I googled [make.sh: 396: [: 1: unexpected operator] and i find bugs reports and in one a user propose a patch for the driver.
I try that with no luck. The weird is that in Alpha 2 release the Catalyst driver was working with jockey.
Thanks.

---

### Post by QIII on 2012-06-21
There is no reason to go through the pain of binary installation if you are running Ubuntu.  AMD and Canonical are good buddies.

If the graphical method does not work, see the link in my signature.

---

### Post by raidensub on 2012-06-21
Thanks for replying but i forgot to post that i have try to install from the command line and i get an error also. I don't remember the error. I am going to reproduced tomorrow. Sorry.

---

### Post by raidensub on 2012-06-22
> **QIII said:**
> If the graphical method does not work, see the link in my signature.

Using this method i get this in the terminal:

[http://pastebin.com/nEFVPU1j](http://pastebin.com/nEFVPU1j)

---

### Post by aceprry on 2012-06-22
My experience with the HD4350 is that I can't get Unity to work under the 3D desktop.  Before you first log in, you have to click on the "button/icon" in the upper right corner of the login box, set the desktop to "Unity 2D", then login.  The desktop will appear and start working, slowly, but it will work.  I think the official AMD drivers work as well, but you have to reboot a few times before it starts to work.  As QIII mentioned earlier, it's easier to use the ubuntu repository drivers.  Good luck.

---

### Post by raidensub on 2012-06-22
My card has no problem to run unity 3d or kde4 with desktop effects if i use the opensource drivers. My problem is that i can't activate the catalyst drivers. Thanks for replying.

---

