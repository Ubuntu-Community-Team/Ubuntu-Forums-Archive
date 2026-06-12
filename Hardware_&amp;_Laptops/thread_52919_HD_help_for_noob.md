---
title: "HD help for noob"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by Forensick on 2005-07-29
Hey guys, I am a total noob to Linux in general and I am having a hell of a time with mounting a hard drive of mine on to Ubuntu. The hard drive in question is a WD 40 gig that stores all of my Mp3's and I dont know if this will help, but the mp3's are in NTFS format. I am really sorry for asking a question that has probably been asked a million times before, and I did read the wiki, but I couldnt make heads or tails from it. Thanks in advance guys.

---

### Post by jasmuz on 2005-07-29
Did you read this:

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

First of you need to know what hd is, hda, hdb or hdc, and what is the number for the partition

Then do this:

1- sudo mkdir /media/Windows

2-sudo gedit /etc/fstab

This example is from my fstab, adapt to your own
/dev/hda1	/media/Windows	ntfs	umask=0222	0	0

or if you are only looking to mount it, and not at every boot.

sudo mount -t ntfs /dev/hdxx /media/Windows  (x is to be substituted)

---

### Post by Forensick on 2005-07-29
The number for the partition? There is no partition on it. As for the name of the hd, I found in device manager and its called "hdb". All this hd has on it is mp3's. I just dont understand why it could be seen in device manager, but not be abled to be accessed .

---

### Post by jasmuz on 2005-07-30
Then mount hdb1, one thing is to be recognized on the Hardware manager and another is to be automagickly mounted wich isnt happening yet on Ubuntu.

---

