---
title: "Scanner not working after kernel upgrade to generic 3.5.0-27 U12.10"
date: 2013-03-25
forum: Hardware
---

### Post by Bargoth on 2013-03-25
Hi,

after kernel upgrade to generic 3.5.0-27 in Ubuntu 12.10, my scanner stopped working. Xsane could not find scanner. 
After reading and checking I found that there is problem with permissions of regular user. 

Check if scanner is visible to the system  user@user: lsusb

then check correct bus number

ls -l /dev/bus/usb/002

Then
sane-find-scanner  gave info that ther no enough permission to access USB

when running sudo sane-find-scanner it was ok.


Solution.
Install Users and groups tool     sudo apt-get install gnome-system-tools

Details [http://askubuntu.com/questions/66718/how-to-manage-users-and-groups](http://askubuntu.com/questions/66718/how-to-manage-users-and-groups)

Then Run users and groups form main panel then click on Manage Groups

I have added user to grups plugdev and scanner.

Everything started working as usual.

I hope that my post will help someone :)

---

