---
title: "USB floppy automount"
date: 2010-06-22
forum: Hardware
---

### Post by s_raiguel on 2010-06-22
Curiously, my USB floppy drive no longer automounts, though it was working normally just a couple of days ago. I can manually mount it on a directory I create using mount /dev/sdh, but this is a bit of a hassle. USB hard drives and memory sticks still mount as usual, but not the floppy. How does one specify automounting behavior in Ubuntu, anyway?

---

### Post by dabl on 2010-06-22
A similar thread here: [http://ubuntuforums.org/showthread.php?t=1511446](http://ubuntuforums.org/showthread.php?t=1511446)

---

### Post by s_raiguel on 2010-06-22
Well, not exactly, dabl. This is a USB floppy drive, not one of the old half-height drives that lives in the case, and that is the issued discussed in the other thread. The drive is clearly recognized, and shows up with lsusb. 

Incidentally, the configuration editor also shows that all the automount boxes are checked in apps/nautilus/preferences (and other USB devices automount as expected). This drive was working fine just two or three days ago, and still does under Windows, so mechanical failure is not the problem. There has been a major wave of updates for Lucid in the last couple of days, and I suspect that something in those updates has produced unexpected consequences.

---

### Post by s_raiguel on 2010-12-19
Months after posting this, I seem to have found the answer, which I thought I'd post in case anybody else has had this issue come up. What worked for me was installing halevt, either from Synaptic, or opening a terminal and entering

 sudo apt-get install halevt

At this point, because the install also starts halevt as root, you're USB floppy will automount and you'll be able to read the disk, but unless you're root, you won't be able to change anything on the disk. Worse, all your USB devices, including USB memory sticks, are now opened with only root permissions and will be unwriteable. To fix this, you need to kill the running instance of halevt and start it with

halevt -u [username]

where [username] is your logon name. If you want halevt to always show this behavior, without having to enter these parameters each time, you need to edit the config file /etc/halevt/halevt.xml by entering 

sudo gedit /etc/halevt/halevt.xml

to edit the config file, and look for the lines that say 

  <halevt:OnInit exec="halevt-mount -u $hal.udi$ -o sync -m 002"/>
and
  <halevt:Insertion exec="halevt-mount -u $hal.udi$ -o sync -m 002"/>

and change these to:    

  <halevt:OnInit exec="halevt-mount -u $hal.udi$ -o sync -m 777"/>
  <halevt:Insertion exec="halevt-mount -u $hal.udi$ -o sync -m 777"/>

Everything should now automount with full user-level access.

---

