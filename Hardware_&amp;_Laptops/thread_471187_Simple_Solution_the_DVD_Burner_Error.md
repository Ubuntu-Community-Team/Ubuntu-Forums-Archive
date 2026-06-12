---
title: "Simple Solution the DVD Burner Error"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by Caytin on 2007-06-11
Since I installed Ubuntu Feisty, I was able to burn CDs but not DVDs.  I have roamed up and down the internet 
looking for a solution, and have finally come across one.

In Terminal:
sudo pico /etc/fstab

when the fstab file pops up, there should be a list of all the media drives on your computer.
Go down to /dev/hdc

if your line for hdc looks like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

change the noauto to auto, and your burner should now work.

If you want to find out what burner you have:
wodim --devices

It should come up with the brand and type of burner you have.

Given I have a Pioneer DVDRW DVR-K15, and I was getting an I/O error when burning.  I do not know if this will work with machines having problems mounting the Blank DVD-Rs.

---

### Post by wingnux on 2007-07-06
It didn't work for me =/ Can't get burn any cd/dvd on linux.

---

