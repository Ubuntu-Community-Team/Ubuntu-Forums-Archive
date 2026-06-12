---
title: "Incorrect metadata area header checksum"
date: 2005-11-10
forum: General Help
---

### Post by ttrygve on 2005-11-10
I've been having trouble figuring out how to get rid of "Incorrect metadata area header checksum" messages.

At first I (foolishly) ignored it, thinking it must not be important since everything appeared to be working fine anyway.  But when I went to add two new drives to my volume group, things got worse, and long story short, I reinstalled to one of those other drives (because I could no longer boot off my original volume group), I then mounted the original LVM to back it up to another system.

Several installs later (no more major problems, mostly just experimenting), I still get "Incorrect metadata area header checksum" every time I use LVM in the partitioning step of the installer.

The below is taken from a fresh install where I set up LVM using the installer, and did not touch it after the install, and immediately after install, I'm still getting these messages.

$ sudo lvdisplay
  Incorrect metadata area header checksum
  Incorrect metadata area header checksum
  --- Logical volume ---
{blah ...}

What can/should I do about this?  I plan to run "badblocks -vw" on the other drives not currently in use (I already ran it on the drive I've just installed to), and then add them to the volume group so I can extend my logical volumes, and have the capacity to restore the stuff I backed up when things first blew up on me, and I am obviously hoping it will go a little smoother this time.

Since I can't seem to set up LVM without running into this problem, I'm surprised I wasn't able to find anything about this in the wiki, forums, or list about this.  Googling showed enough people who had this problem along with others, but I didn't find a solution to just this (or even a clear explanation for what it means, which probably would have helped my search), and only [ couple](http://www.google.com/search?num=100&complete=1&hl=en&lr=&safe=off&q=%22Incorrect+metadata+area+header+checksum%22+inurl%3Aubuntu&btnG=Search) of the pages google found were related to Ubuntu.

Any suggestions?

---

### Post by Enki on 2005-11-26
I had the same problem. It was because of LVM checking my /boot partition, which it shouldn't because this partition is not (and cannot be) part of a volume group.

exclude it by editing /etc/lvm/lvm.conf :
```
filter = [ "r|/dev/cdrom|", "r|/dev/hda1|" ]
```
where hda1 is your boot partition

afterwards run vgscan

BTW: This may have been caused by me trying different partitioning schemes during the install. The whole process is not very intuitive and IMO, this is one area where the installer could use some polishing up.

---

### Post by gunnor on 2007-06-25
Enki,

Thank you very much for the information, it saved my life! :grin:
I've had the same message and was close to zero down the LVM! :shock:

---

