---
title: "Mount AND use USB drive at startup?"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by mdroz on 2006-08-17
[FONT="Arial"]How do I set Ubuntu 6.06 to mount a USB drive at startup AND make it available for use immediately.  To clarify, here’s what’s going on.  My fstab has this line:[/FONT]

[FONT="Courier New"]/dev/sdb5  /bak  ext3  auto,rw,user,suid,dev,exec  0  0[/FONT]

[FONT="Arial"]This seems to work fine for getting the drive to mount at startup.  However, when I ssh into the system and browse the /bak directory, it’s empty.  Webmin (Disk and Network File Systems module) does confirm that the drive is set as a permanent mount, but it also tells me that the drive is NOT In Use.  When I set the In Use flag to Yes, I can go back in the terminal and list the contents of the /bak directory.  

Double-clicking on the drive icon on my Gnome desktop has the same effect of enabling the drive (making it “in use”).  The problem is, this is my file server and I don’t want to have to log in to make the drive/mount usable.  I would like to be able to have the system start up and use the drive automatically, so I can run some cron jobs to back up my files.

What am I missing?  Is it possible to make a USB drive available automatically?

TIA[/FONT]

---

### Post by kszys on 2006-08-25
Same problem here - I have to login to make the USB drive usable... Anybody any ideas?

---

