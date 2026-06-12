---
title: "Help with copying music off my iPod."
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by PheonixRising on 2005-12-12
I'd like to copy the music off my iPod and onto my computer so that I can wipe the iPOd clean and start on a clean slate. What is the best way to do this? Note that I am a Linux noob so you'll have to explain quite a bit of stuff to me (I imagine), and I have no Windows Partition and a large amount of AAC files, my iPod is a Windows 4-th gen Photo iPod if that matters. So help with this would be greatly appreciated. And after that, if you could teach me the best way to use an iPod with Linux, that would be greatly appreciated as well.

---

### Post by aysiu on 2005-12-12
Well, first things first. When you plug your iPod in, does it automount and appear as an icon on your desktop?

---

### Post by PheonixRising on 2005-12-13
Hopefully these two screenshots answer your question:

[[IMG]http://img202.imageshack.us/img202/3394/screenshot2sq.th.png[/IMG]](http://img202.imageshack.us/my.php?image=screenshot2sq.png)

[[IMG]http://img227.imageshack.us/img227/8740/screenshot14eo.th.png[/IMG]](http://img227.imageshack.us/my.php?image=screenshot14eo.png)

I'm slightly confused as too why I have so many iPods showing in "Computer"

---

### Post by aysiu on 2005-12-13
Click on the Gnome menu and go to Places > Search for files and folders and then in **Name Contains**, put *.m4p and then in **Look in Folder**, select Other... and navigate to your mounted iPod.

You may also have to go to **Available options**, and select Show hidden and backup files and then **Add**

Once you find all your music, copy and paste it all into a folder somewhere.

---

### Post by PheonixRising on 2005-12-13
Cool, thanks, but all the files have wierd 4 letter names, what is up with that?

And what program should I use to import this stuff?

How do I wipe my iPod clean on Linux?

---

### Post by aysiu on 2005-12-13
[QUOTE=PheonixRising]Cool, thanks, but all the files have wierd 4 letter names, what is up with that?[/quote] I don't know what you mean by weird 4-letter names. To be safe, I guess you could just search for *.* instead of *.m4p.

> 
And what program should I use to import this stuff? You don't need a program. Once the files are found, just highlight them all, and copy and paste them into a folder.

> 
How do I wipe my iPod clean on Linux?Unmount your iPod by right-clicking it and selecting "unmount volume." Install GParted ```
sudo apt-get update
sudo apt-get install gparted
``` and then run it: Alt-F2, then ```
gparted
``` Select the iPod and delete the partition.

---

### Post by PheonixRising on 2005-12-13
For some reason, Gparted can't read the filesystem and does not register any partitions on the iPod. What should I do?

---

### Post by aysiu on 2005-12-13
[QUOTE=PheonixRising]For some reason, Gparted can't read the filesystem and does not register any partitions on the iPod. What should I do?[/QUOTE] Have you already successfully copied all the songs off of the iPod?

---

### Post by PheonixRising on 2005-12-14
Yes, I have.

---

### Post by blochsound on 2008-01-31
I think that is apple's way of obfuscating the songs on your ipod.
If you right click on any of the XFEQ.m4a files (or whatever) you will see that all of the metadata is intact, its just the file names that have been garbled.  I just went to ipod control/music/ and then copied all of the folders and subdirectories.

GTKpod will suck all of the songs off of your ipod, although it hiccups on copying the encrypted files (haven't figured it out yet)

---

