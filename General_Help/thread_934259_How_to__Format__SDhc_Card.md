---
title: "How to  Format  SDhc Card ?"
date: 2008-09-30
forum: General Help
---

### Post by Sonah on 2008-09-30
[FONT="Arial"][B][SIZE="3"]hi 
i have UbuntuEEE 8.04

How  to "Format"  my SDhc 8G Card ?

I always get "Permission error" when i try to delete a file in SDhc  ?

also how to change file type from EXT3 to FAT32 ?[/SIZE][/B][/FONT]

[IMG]http://i36.tinypic.com/2hplqvc.png[/IMG]

---

### Post by zzzzz1 on 2008-09-30
gparted > unmount the SD card and you should be able to format it
just done it with mine


If you dont have it you can install it from add/remove software or with
> 
sudo apt-get install gparted

---

### Post by luotinen on 2009-09-17
I used gparted to format my 16GB sdhc card for Canon EOS 450D (it seems to be unable to format SDHC cards). 

So just type "sudo gparted" to shell and find your card from right (be sure you have the correct drive selected). Then delete whatever is currently on card and create a new partition with FAT32 filesystem. I named mine EOS DIGITAL like Canon cameras, but I'm fairly sure any name will do...

This method should also work for other models like 1000D or 500D for example.

---

### Post by spyrosebastos on 2009-09-30
Question:  how have you guys gotten your sdhc cards to be recognized in order to format... I've had an 8gb stick for months now for no reason.  ubuntu/windows/fedora on two different computers and 3 different phones i've tried haven't been able to even detect it.  suggestions?

gparted doesn't and disk usage analyzer dont work; sdhc card doesn't show up under devices.

Every other memory stick shows up immediately under 'Places' or in the 'Computer' gui heirarchy; except the one i spent $ on.

---

### Post by Chronon on 2009-09-30
Sounds like a broken memory stick.

---

### Post by mn_voyageur on 2009-12-17
When I update to Karmic, my Ricoh media readers began to work.  Under Jaunty, I could not get them to mount.

MN

---

### Post by tgalati4 on 2009-12-18
I've had a similar experience with sdhc cards.  Gparted will happily format them to anything you want.  BUT, the internal flash controller only operates with the correct Heads, Cylinders, Sectors count.  How do you get this count?  You have to get a similar card and see what the correct CHS count is or searth the tubes.

man fdisk 

Use fdisk with the appropriate CHS settings and Voila! Your expensive, high capacity card is now readable and writable.  I was pissed that I had trashed a card only to determine that the CHS counts were different between a virgin SDHC card and a borked one. 

I think gparted uses CHS counts that are OK for real hard disks but cause SD cards to puke.  With the correct CHS counts you can use FAT16, FAT32, EXT2, or EXT3.  I've used them all in capacities between 1GB and 4GB in my Nokia n800.

Digital camera's, mp3 players, and other devices normally want FAT16 or FAT32.

Sometimes you can revive a card by formatting in a digital camera.  They are obviously programmed to use sensible CHS counts when reformatting.

Good luck.

---

