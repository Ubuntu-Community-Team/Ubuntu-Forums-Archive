---
title: "mount problems"
date: 2008-11-19
forum: General Help
---

### Post by The_Dark_Lord on 2008-11-19
I have another harddrive and partion on this system. up till a few weeks ago when ever i mounted these it asked for my password before so but now it just mounts them without asking for the password.

Any Help appreciated

---

### Post by taurus on 2008-11-19
Did you happen to run sudo with something a few minutes before you tried to mount that partition?

---

### Post by The_Dark_Lord on 2008-11-20
im security paranoid so i have sudo set to ask everytime its only on mounting it doesn't do it.
Although come to think of it i think i told it to same the password on the on the box that came up last time it asked. anyway to reverse that?

Ubuntu 8.04

---

### Post by The_Dark_Lord on 2008-11-25
can anyone help me?

---

### Post by bodhi.zazen on 2008-11-25
What box are you talking about, how did you mount the partition ?

Probably not what you are asking for, but you could always change your partition.

What do you have set in /etc/fstab for the partition in question ?

---

### Post by The_Dark_Lord on 2008-11-27
I have Ubuntu 8.04, i mount it by going places then choosing the partition, it used to ask for a password when doing that but now it doesn't

I have never edited the fstab file as i have never needed to
Here is my fstab file

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ad903dd3-7a07-46f9-bfeb-27eb076a3f66 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=39110e6e-df1f-495b-9e8e-246ceac74a51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# 1002 is the USB group ID
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

---

### Post by drs305 on 2008-11-27
Does 8.04 have the System, Admin, Authorizations option? I'm on my Intrepid box at the moment. Under freedesktop, hal, storage there are authorization options which you can edit or return to default.

---

### Post by The_Dark_Lord on 2008-12-18
Never Mind, i updated to 8.10 and its all good now

---

