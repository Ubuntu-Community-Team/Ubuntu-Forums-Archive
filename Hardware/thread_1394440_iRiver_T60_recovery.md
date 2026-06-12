---
title: "iRiver T60 recovery?"
date: 2010-01-30
forum: Hardware
---

### Post by ethanay on 2010-01-30
I am not sure if this is the best place for this thread, but I am starting it here:

The situation:  A few days ago my iRiver T60 stopped working.  It turns on with no screen.  After "turning it on" I can move the hold button, which activates the screen.  The hold icon (a little lock on the screen) registers on and off with the button.  The screen itself displays ```
"file check error"
```  No other buttons are responsive.  The power button does not turn it off again.

Fortunately, Windows and Linux (Ubuntu!) still detect it as a normal flash drive, so I did not manage to fully "brick" it (unlike that print server a week before...).  I tried reformatting it with gParted, but the disk appears as a "corrupt" file system.  I believe reformatting erased the T60 OS, so now the player functions only as a batter-powered USB drive.

I tried the Windows software for recovery (in Windows; won't work through Wine):

1. Firmware Updater says it doesn't recognize the device id = MP3 T60___.  
2. iRiver Plus 3:  I tried "reinitialize the disk," but all that does is add in the folder structure without any firmware.  "Update firmware" in this software only returns a network error.
3. CrossUpdater appeared to work, but only loaded the .hex file, which the player was in no state to handle.

Because the player still turns on and is recognized as a USB device, and I can transfer files to and from it, I am hopeful that the problem is fixable.

Hypothesis:  The system file became corrupt.  Deleting and reformatting it made the problem worse :8-[  If I can borrow and install either
1. a working system file OR
2. the complete disk image from a working T60 device (including all hidden files)

Maybe the drive will work again?  

iRiver support wants $60 to fix the device, so if I am unable to fix it, I may just "invest" in a new device like the Cowon iAudio 7 for a few dollars more.

---

### Post by henriquemaia on 2010-01-30
Well, by the description you make of the problem, you seem to be facing a hardware problem instead of a software one. I had something similar in mine (some files got corrupted) but the device came ok after formatting it.

I've sent you the image as PM. I hope you can solve that.

---

### Post by ethanay on 2010-01-31
As a warning, I barely know what I'm doing.  I know just enough to be dangerous.  So feel free and post explanations/corrections.  Here's what happened in order to fix the player:

I received a working iRiver T60 4gb disk image from someone on the Ubuntu Forums (thank you!).  They used partimage in order to create the complete disk image.  

They provided an fdisk -l output of their player with the image.  I used fdisk to take a look at partitions on my player as well:

```
sudo fdisk -l /dev/sdb1
```

Next I saved both the files in a folder, named "fdisk_4gb" and "fdisk_2gb" respectively.  Just for kicks, I compared the images:

```
diff -i -w -y fdisk_4gb fdisk_2gb
```

The -y switch is very nice for comparing differences in two separate columns:

```
Disk /dev/sdb1: 2006 MB, 2006936064 bytes		      |	Disk /dev/sdc: 4023 MB, 4023386112 bytes
255 heads, 63 sectors/track, 243 cylinders		      |	124 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes	      |	Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x6f20736b				      |	Disk identifier: 0x74756f20

This doesn't look like a partition table			This doesn't look like a partition table
Probably you selected the wrong device.				Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  Sys	   Device Boot      Start         End      Blocks   Id  Syste
/dev/sdb1p1   ?       48437      119493   570754815+  72  Unk |	/dev/sdc1   ?      150662      221445   272087353   6f  Unkno
Partition 1 has different physical/logical beginnings (non-Li	Partition 1 has different physical/logical beginnings (non-Li
     phys=(357, 116, 40) logical=(48436, 183, 40)	      |	     phys=(368, 115, 53) logical=(150661, 81, 58)
Partition 1 has different physical/logical endings:		Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(119492, 104, 7)	      |	     phys=(357, 114, 52) logical=(221444, 1, 19)
Partition 1 does not end on cylinder boundary.			Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       10501      131013   968014120   65  Nov |	/dev/sdc2   ?      238766      460164   851054640+  6f  Unkno
Partition 2 has different physical/logical beginnings (non-Li	Partition 2 has different physical/logical beginnings (non-Li
     phys=(288, 115, 43) logical=(10500, 111, 30)	      |	     phys=(355, 105, 51) logical=(238765, 28, 33)
Partition 2 has different physical/logical endings:		Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(131012, 158, 28)	      |	     phys=(10, 255, 13) logical=(460163, 52, 1)
Partition 2 does not end on cylinder boundary.			Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?      116395      236907   968014096   79  Unk |	/dev/sdc3   ?      230079      230079        1286+  70  DiskS
Partition 3 has different physical/logical beginnings (non-Li	Partition 3 has different physical/logical beginnings (non-Li
     phys=(366, 32, 33) logical=(116394, 188, 12)	      |	     phys=(288, 108, 33) logical=(230078, 63, 52)
Partition 3 has different physical/logical endings:		Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(236906, 234, 25)	      |	     phys=(114, 47, 32) logical=(230078, 105, 20)
Partition 3 does not end on cylinder boundary.			Partition 3 does not end on cylinder boundary.
/dev/sdb1p4   ?           1      226407  1818613248    d  Unk |	/dev/sdc4          375349      375356       27235+   0  Empty
Partition 4 has different physical/logical beginnings (non-Li	Partition 4 has different physical/logical beginnings (non-Li
     phys=(372, 97, 50) logical=(0, 0, 1)		      |	     phys=(0, 0, 0) logical=(375348, 92, 25)
Partition 4 has different physical/logical endings:		Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(226406, 223, 57)		      |	     phys=(0, 0, 0) logical=(375355, 102, 59)
Partition 4 does not end on cylinder boundary.			Partition 4 does not end on cylinder boundary.
```

Yet more hope that I did not fully "brick" my player, as even with the differences, the weird partition table looks intact.  In contrast, gParted shows one FAT16 partition.  However, partimage gave me an error telling me that I could not restore the image to a partition of lesser size than the partition on which it was created:  4gb > 2gb.  Doh!

When that failed, I tried to restore only the complete MBR from the partition image using partimage again.  Partimage gave me two options for the destination partition:
```
/dev/sda
/dev/sdb
```

/dev/sda is my hdd.  I chose /dev/sdb, my player (unmounted).  It gave me three options for the MBR source:
```
/dev/sda
/dev/sdb
/dev/sdc
```

This confused me, because I thought I had already pointed it to the source (the T60.000 image file).  Understanding from the fdisk output that the T60.000 image was taken from a /dev/sdc (and I had no /dev/sdc on my system), I chose that option.

I finished up, unplugged the player....and the "hold" button caused the screen to display the usual (working!) "HOLD" message.  I turned hold off, and booted the player.  The screen printed ```
iRiver T60 - 4gb
``` Curious, but at that point I didn't care because it was a WORKING PLAYER!  There were some weird characters on the screen, and the folders were all messed up.  So I reset all defaults and reformatted the player, and it cleared the display issues.  I rebooted again and it displayed ```
iRiver T60 - 2gb
```  Back to normal.  I am now listening to music on my player.

I am curious whether it would have worked if I just copied the T60.sys file to the player vs restoring the entire MBR?

I will use partimage on my empty player to create a small restore image in case I ever need to revive it again.

---

### Post by curbat on 2010-02-02
Greetings to all.
It is possible? To send to me too image-file t-60?
I also have problems with restoration Iriver

---

### Post by ethanay on 2010-02-03
hello Curbat,

I uploaded a zipped image of my 2gb T60 that I made after restoring it (see attached file).  You need to unzip it, and then use it to restore the MBR using partimage.

Good luck!

ethan

---

### Post by Gobsmacked on 2010-02-06
ethanay, thank you so much! 
I restored my T60 with your image :D

---

### Post by ethanay on 2010-02-08
wonderful! glad it is useful!  :)

---

### Post by karmagednb on 2010-04-03
Hi, sorry my bad english.. 

I have a Iriver t60 - 1gb and I have the same problem posed here. I tried partimage and the file you posted it, but as the match gb, I can not do anything. I wonder if they have the image of 1GB? It really would be very grateful!

A greeting and a hug from Latin America!

---

### Post by ethanay on 2010-04-04
hi karmagednb,

this part of my post is relevant to you -- use the MBR restore feature rather than full disk image restore:

> However, partimage gave me an error telling me that I could not restore the image to a partition of lesser size than the partition on which it was created: 4gb > 2gb. Doh!

When that failed, I tried to restore only the complete MBR from the partition image using partimage again. Partimage gave me two options for the destination partition:
```

/dev/sda
/dev/sdb
```

/dev/sda is my hdd. I chose /dev/sdb, my player (unmounted). It gave me three options for the MBR source:
```

/dev/sda
/dev/sdb
/dev/sdc
```

This confused me, because I thought I had already pointed it to the source (the T60.000 image file). Understanding from the fdisk output that the T60.000 image was taken from a /dev/sdc (and I had no /dev/sdc on my system), I chose that option.

I finished up, unplugged the player....and the "hold" button caused the screen to display the usual (working!) "HOLD" message. I turned hold off, and booted the player.

---

### Post by reincidente_ on 2010-04-16
steps to restore the MBR


1- install partimage
```
sudo aptitude install partimage
```

2-run partimage
```
sudo partimage
```

3-select the partition to restore, the file to use and the action

[[IMG]http://img59.imageshack.us/img59/4823/pant1q.png[/IMG]](http://img59.imageshack.us/i/pant1q.png/)

remember the id of the partition(in my case is sdb)

f5 to continue

4-select in the two cases the id to corresponds(in my case is sdb).
restore what? MBR
[[IMG]http://img52.imageshack.us/img52/4899/pant2.png[/IMG]](http://img52.imageshack.us/i/pant2.png/)


f5 to continue
[SIZE="5"]
and now umount the iriver[/SIZE]. then accept the warnigs. and finished

hope this will be useful 
sorry for my english
Greetings from chile

---

### Post by loyal4dna on 2010-04-16
thank you

---

### Post by evgeny.ger on 2010-10-15
I tried recovery by copying MBR using partimage tool and attached image, but I have 4 GB version of iRiver T60. Though my player was unbricked, I can use only 2 GB of player memory (file manager shows that I have 2 GB free space on my volume). Better than nothing, but worse than before. I tried to use parted and gparted, but both of them show that I have only one volume, with size of 4GB.

Can anybody attach 4 GB T60 image or explain how to fix MBR?

---

### Post by ethanay on 2010-10-16
First off, as the OP, I'm so glad to see that this thread is so useful to so many people!  Ubuntu Forums, Ubuntu, GNU/Linux, and Free Open Source Software all are wonderful!

Second, for evgeny.ger:

My player was 2gb, and I recovered it using a 4gb MBR.  It displayed "iRiver 4gb" 

after I reformatted it under the options menu in the player, it reset itself back to 2gb.  So you might try to reformat/reset to factory default your player using the same menu option in the player.

Good luck!

---

### Post by miloshimeck on 2011-03-08
Hello everybody,
I am happy that I discovered this threat. I have the same problems with my iriver. I made step by step (by tutorial of reincidente_) until step 4 here I have problem.

[https://picasaweb.google.com/lh/photo/oPRIU2VI1y_sg10UKIGSGd68XTZf4nb0mKW08bqXvCY?feat=directlink]("https://picasaweb.google.com/lh/photo/oPRIU2VI1y_sg10UKIGSGd68XTZf4nb0mKW08bqXvCY?feat=directlink")

sda and sdb are my HDD and sdh is iriver. In this point I am lost. Where Iam mistaken?

---

### Post by ethanay on 2011-03-08
Hi miloshimeck,

have you tried these instructions here?
[http://ubuntuforums.org/showpost.php?p=9131192&postcount=10](http://ubuntuforums.org/showpost.php?p=9131192&postcount=10)

my guess is that you selected the wrong drive/partition to restore on the first screen, and so don't have the options you need later on?

if not, hopefully someone else can provide a hint!

ethan

---

### Post by miloshimeck on 2011-03-12
Yes I follow those instuctions, and properly select the right/partition.

---

### Post by miloshimeck on 2011-03-16
Hi,
on my desktop PC, partimage didnt work, still I dont know why. So I tried to install on notebook and works. mp3-player play =)
Thanks a lot, all of you.

---

### Post by ethanay on 2011-03-17
ok, great!  so it was potentially a hardware issue. i'm glad you found a work-around and are posting back your results!

---

### Post by dizzy_radu on 2011-07-14
> **ethanay said:**
> hello Curbat,

I uploaded a zipped image of my 2gb T60 that I made after restoring it (see attached file).  You need to unzip it, and then use it to restore the MBR using partimage.

Good luck!

ethan

can you please upload the 4gb version? it's kinda my last hope here ...
thenks!

---

### Post by ethanay on 2011-07-14
hello, i don't know what i did with the 4gb image file.  you should be able to use your 2gb to restore and then reformat (via T60) or resize (using parted) it to recognize the total 4gb?

let us know!

---

### Post by dizzy_radu on 2011-08-06
workend like a charm.
followed @reincidente_ instructions to the letter and ubuntu did in 5 seconds what windws couldn't do in 5 hours
thenks guys for all the help... great thread... even better support
cheers all :D

---

### Post by Andre Dom on 2012-01-03
&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;

---

### Post by Raven_Oscar on 2012-04-28
Thanks for image. It really helped.

---

