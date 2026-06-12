---
title: "Cannot find Windows partition in Aspire One"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by mantd on 2009-11-02
Hi,

I've been trying to install ubuntu netbook remix on my new aspire one. It came with XP preinstalled on a 160gb hdd.

The problem is i couldnt find my windows partition to resize. On windows disk manager there is 2 partition on the drive PQSERVICE (unmountable/hidden 6g) and my xp partition (143g). In gparted its says /dev/sda unallocated space of 143gb. I've attached a picture of my gparted running on liveusb. 

I tried wubi but it couldnt get past the partition setup. The error message is no root file system is found.

I don't want to lose the files on the windows partition thus the resizing or wubi method.

Appreciate if you could help me or point me to right direction. I've been searching for links in the forum and the web to no avail (yet).

Thanks.

-Erman

---

### Post by wilee-nilee on 2009-11-02
That is strange I have a acer net-book and was able to modify the partitions with gparted in order to install. I suspect that the usb was not imaged correctly or the original iso is corrupted. so you might try reimaging the usb stick if that doesn't work try another download and reimage the usb stick. There are no blocks by acer to installing other OS. So I assume the image your showing is from running the usb live. The net-book remix was problematic for a while I assume it has been fixed but I switched to a regular install it runs faster then the net book mix which started to act really wierd a couple of days before the Karmic release. So is this usb Karmic.

---

### Post by mantd on 2009-11-02
Thanks for the reply, Wilee.

Image was taken from me running the live usb.

I am trying to download from a torrent source now. Previously i've tried from 2 other mirrors. i've checked the hashes its all ok. 

I've also tried partition magic to resize to no avail also.. 

Might it be a problem with my hard disk ?

-Erman

---

### Post by wilee-nilee on 2009-11-02
> **mantd said:**
> Thanks for the reply, Wilee.

Image was taken from me running the live usb.

I am trying to download from a torrent source now. Previously i've tried from 2 other mirrors. i've checked the hashes its all ok. 

I've also tried partition magic to resize to no avail also.. 

Might it be a problem with my hard disk ?

-Erman

 It is possibly a problem with the HD but probably not that shouldn't keep gparted from reading it. I have done downloads that passed all the tests but just didn't work. If you can delete the partition on the stick put a new fat 32 on there before imaging you will be more likely probably to get a good image, I always reformat the partitions on thumb drives or any thing I use before installing, hope it all works.

---

### Post by mantd on 2009-11-02
Hello Wilee,

I've downloaded the torrent and checked the hashes, ok.

I tried making a usb image from windows, it wasnt able to boot.

I made a usb stick boot drive under my ubuntu 9.10 machine now it went okay.

Booted okay, checked the image went ok as well. 

Under gparted, the drive still says unallocated partition 149gb. 

I tried paragon partition manager for windows its says the windows partition is invalid ...

Any other suggestion ?

---

### Post by wilee-nilee on 2009-11-02
I am stumped on this you might try the acer forum they have a Linux section as well as support for other OS. [http://www.aspireoneuser.com/forum/](http://www.aspireoneuser.com/forum/) So did you reformat the thumb in between the windows usb imaging and the Linux one, I always reformat just to make sure everything is gone. In the Ubuntu usb imager you can leave a portion open for making it a bootable usb that can get more information like updates, you might try running a update and I don't know if gparted could be reinstalled. You can repartition in XP so that might be an option if you have an empty space it may recognize it. When I got my acer it seemed to be corrupted although I was able to install Jaunty 1st then karmic, but grub shows the reformat partition and I was able to just click on that to reformat the main XP OS, so you can overwrite the XP with the reformat partition. The reformat partition can be run from XP to overwrite itself I never tried because I had already installed Jaunty and just happened to click on the formatting partition to see if it would reimage the main XP OS. Worse case scenario if it is brand new and you can return it that is what I would do, but it is hard to tell where the problem is that is not letting gparted recognize the XP. I don't remember if mine was the same way and I just resized it then left an open partition to install to, but I think that may have been the case. If you shrink the partition you shouldn't cause any damage to the 2 XP partitions. Will it allow you to resize, if so if it was me I would go for it because if gparted allows you to resize then it should allow the partition manager in the install to recognize the open space then install 9.10 in it as a side by side using the slider at the bottom to set it exactly as you want it. I hope this make sense I have some ideas here but I think this last one is probably the answer the acer forums could confirm the empty looking partitions from your 1st screen shots, hopefully advise you. There is a mod from here that posts there. You can also just click on the install button and get to the partitioning part of the install and see if it will allow you set both OS side by side and use the slider to format the sizes as long as you don't hit the go button here you can abort with no change to the original setup. I think that gparted not recognizing the XP is probably normal it just seems wrong but if you can resize I think your okay especially if you try to see if you can do it from the install partitioner. After looking at the screen shot again I realized that a unallocated partition probably can't be resized.

---

### Post by wilee-nilee on 2009-11-02
So you might also try downloading a regular Karmic iso and seeing if it is doing the same thing. I wish I new the definitive answer to this, as my acer aspire is a nice little unit.

---

### Post by mantd on 2009-11-02
yeah, i formatted the usb drive to fat32, everytime.

I've tried using the ubuntu desktop cd 9.04 and also 9.10 cd to install wubi. The same error "no root file system found".

I am trying acronis disk director now to resize the partition. It can detect my partition. Resizing as i am writing. so far so good.

I will try with wubi after the partitioning. Hope it will work.

Will keep u posted. 

I've encountered this gparted problem before on a friends laptop (an old ibm laptop), but his was a corrupted partition. It didnt appear on gparted too.

---

### Post by mantd on 2009-11-02
After running the partition manager, I finally got wubi running on my Aspire One...

But can't seem to get the wifi driver to install... its weird 
because under live usb wifi driver is available.

Also now I can see all my partitions (PQService, My XP partition and my data partition(The one i created with the disk Manager). I presume somehow the disk manager has repaired my partition.

I am trying the wubi desktop 9.10 version next before i go full install.

---

### Post by wilee-nilee on 2009-11-02
So I am confused as to why you would need to manually partition then try to install wubi. Wubi has it's own partitioning method. If you were able to repartition the Hard Drive. If you left a open space, then the XP is now smaller and you have 9.10 running inside of it.

---

### Post by mantd on 2009-11-05
Hi wilee,

Initially wubi install came out with error no root file system defined. 

Also under live usb, my xp partition was not there, gparted says unallocated space. 

After running a couple of windows based partition manager i finally could make another partition to install.

The weird thing is after making another partition, Gparted now sees all three partition in live usb mode. Any ideas whats the cause of it ? A corrupted or hidden filesystem ? I am using the same live usb.

So i am testing under wubi first and it installs fine except i can't browse my network (1 running ubuntu 9.10 and 1 running XP) I can see them, but i can't browse. 

Will be doing a full install soon, over the weekend ... :)

Thanks for helping .. :)

---

### Post by heimio on 2009-11-05
Same behavior on my Asus 1000HG. I have a clean W7 Installation on a brand new 400GB Disc and the Netbook Remix says the whole hdd space is unallocated. 
I made another partition on the netbook but the error persists. I will also try to install a regular 9.10 Image now. I read at least one other post with the same problem (beside yours)

---

### Post by mantd on 2009-11-06
Update:

I've successfully installed ubuntu netbook remix 9.10 on my new ext4 partition. 

Helmio,

I am guessing there must a hidden mode or something within the netbook partition. I have no idea really, its baffling. I must have unlocked it somehow. Maybe someone could enlighten us. 

You could try using netbootin to make the usb boot instead of the usb creator that came with the cd. I had trouble making a good image from the default tool.

---

