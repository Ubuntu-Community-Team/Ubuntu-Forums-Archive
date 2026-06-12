---
title: "USB external hdd?"
date: 2008-07-01
forum: Hardware
---

### Post by gkc01 on 2008-07-01
Hello all,

I was a windows user but now a Linux enthusiast and was wondering if anyone could help me out?

I'm running Ubuntu 8.04 desktop, I use the desktop version as it has a gui so I can http to the server interface if need be. I have an external USB hdd that connects to the notebook, but here is my question.

In windows you can assign a drive, a drive letter further down the line which is not likely to be used by any other device or drive that may be plugged in.

How would one ensure that the external USB hdd is always mounted with the same details to ensure the drive location will not change?

Thank you,

Greg

---

### Post by zalberico on 2008-07-01
In gnulinux the drives are given names instead of letters like /dev/hda for one drive and /dev/hdb for another.  The information about this is stored in /etc/fstab.

Here's a link I found that explains how to edit that:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I think you may be able to rename your USB external there to something that you know is not used elsewhere, unfortunately I do not know if that is necessary or not.

Hopefully someone else will also help you out!

good luck
z

oh and since this is your first post welcome to the gnulinux community

---

