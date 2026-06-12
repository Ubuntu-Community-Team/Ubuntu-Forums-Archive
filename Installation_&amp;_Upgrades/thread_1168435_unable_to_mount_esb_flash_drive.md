---
title: "unable to mount esb flash drive"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by milio1401 on 2009-05-24
Hi guys i have the next question,i recently reinstalled ubuntu intrepid 64 after my jaunty installation failed,and at the same time  i convinced my cousin  to install ubuntu ,it's also intrepid 64,he backed up some files on a usb lexar flash drive,i guess it got corrupted i don't know,it says
Unable to mount LEXAR
 DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

then i get the next window ,i uploaded itso you can see it

i tried to mount itwith the next command  but it didn't work

:~$ ntfs-3g  /dev/sdb1  /mnt/LEXAR
Error opening '/dev/sdb1': Permission denied
Failed to mount '/dev/sdb1': Permission denied
Please check '/dev/sdb1' and the ntfs-3g binary permissions,
and the mounting user ID. More explanation is provided at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

i mean i know it says i like take it to a windows pc and reboot it like two times,and check some stuff,but i don't have access to a windows pc,is there a workaround or something you can do for me?,i mean using ubuntu

---

### Post by milio1401 on 2009-05-24
come on guys don't let me down,if there is no workaround let me know,i want to konow.

---

### Post by triffle on 2009-07-06
Hey Everyone... I was having this same problem. Mine started when I created a "usb startup disk" so after alot of forum searching a googling... i finally found a fix that worked for me.... Here is the link... [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) please see after installing for the fix.

I guess what happens is that while booting from a usb flash drive you trick ubuntu into thinking that it is the CD Rom. You have to go into and edit your /etc/fstab from terminal

sudo gedit /etc/fstab

you will see a line towards the bottom of the page 

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

just put a comment in front of the line like this

#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

save and close

try and put your thumbstick back in and for me anyways tahh dahhh... Word!!!

Much Thanks to the ubuntu community...

---

