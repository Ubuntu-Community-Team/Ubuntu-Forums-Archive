---
title: "CD doesn't autostart"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by Sheytan on 2005-09-23
Before i followed the ubuntuguide "Q: How to speed up CD/DVD-ROM?"

# Read General Notes
#

e.g. Assumed that /dev/cdrom is the location of CD/DVD-ROM

#

sudo hdparm -d1 /dev/cdrom
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
sudo gedit /etc/hdparm.conf

# Append the following lines at the end of file

/dev/cdrom {
       dma = on
}

The cd icon pop up on the desktop and autostart worked

But after it only shows up after i click on the CD-Rom drive in computer folder
I have both cdrom and cdrom0 in inte dev folder.

Anyone knows what i did wrong?

---

### Post by Cyrus on 2005-10-19
My problem is that my CD always autostarts - can I disable that? Is there a general option or do I have to set this for each drive?

What I also would like to know is: It is possible to turn off the automatic close of the drive?

I am using Breezy Badger 5.10

---

### Post by Cyrus on 2005-10-20
Guys, don't let me stand in the rain please ... :D

---

