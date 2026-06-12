---
title: "new to Ubuntu with Dell laptop"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by steel_lady on 2006-05-24
I am buying Inspiron 6400:

Intel ® Core Duo T 2400 (1.83 GHz, 667 MHz, 2 MB L2 cache)
TFT 15.4" WXGA (1280 x 800)
1024MB 533MHz DDR2 SDRAM (2x512)
80GB (5,400 rpm) Hard Drive
Fixed Internal 8X DVD+/-RW
Graphic card Intel Media Accelerator 950 hasta 256MB shared memory
Intel Pro WLAN 3945 Internal Wireless (802.11a/b/g 54 Mbps) for Duo Processors
Bluetooth

I am planning to put dual boot with Windows and Ubuntu

My questions are:

1) Ubuntu or Kubuntu?
I am a blond that needs Linux for work but I prefer something easy to use and that will support all my hardware without necesity to do some additional things with installation

2) Does Ubuntu read Windows? How to organize pertitions and their order?
My necesities are: For working with Linux, I need a storage where I will keep big files for my work. For Windows I also need a storage for movies and other multimedia files. I also need sharing between these two systems. How should I organize my 80G? I prefer to have Linux system alone on its partition, Windows alone on their partition and one big storage to share. But then, do I have to put share storage as FAT32? They told me that that format is not good for big files. Also there is a problem with permissions (I experienced that problem in Red Hat Enterprise, I don't know how it is with Ubuntu...). Can the storage be of some other format? Does someone have some better solution?

3)All additional advices that you can give me for installation of both systems on this kind of machine. Will I have problems installing wifi and bluetooth, graphics etc? How is compatibility of this kind of laptops with Ubuntu? (I had Compaq and Red Hat, never again in my life I will see neither of those two!!!)

---

### Post by an.echte.trilingue on 2006-05-24
1)  Different folks, different strokes.  Ubuntu has more polish, kubuntu is more fun (I think).

2) Fat will not allow files bigger than 3.2 GB.

NTFS read write is possible, but not 100% reliable.  See this page for details:
[https://wiki.ubuntu.com/NTFSReadWrite](https://wiki.ubuntu.com/NTFSReadWrite)


This is how I would partition the 80 GB:
HDA1: 10GB/NTFS.  Install windows here (first)
HDA2: 6GB/ EXT3.  When you install Ubuntu, make this your / partition.
HDA3: 1GB/ SWAP
HDA4: the rest/NTFS or FAT.  This will be the share drive.  When you install Ubuntu put /home here.

3.  Everything but your wireless should work out of the box.

---

### Post by steel_lady on 2006-05-24
>1)  Different folks, different strokes.  Ubuntu has more polish, kubuntu is more fun (I   >think).

Which is easier for stupid blonds?

>HDA3: 1GB/ SWAP

Isn't it better 2G of swap?

>HDA4: the rest/NTFS or FAT.  This will be the share drive.  

which one better, NTFS or FAT?

>3.  Everything but your wireless should work out of the box.

what should I do for wireless?
Bluetooth will work?

---

### Post by charles.figura on 2006-05-25
[QUOTE=steel_lady]>1)  Different folks, different strokes.  Ubuntu has more polish, kubuntu is more fun (I   >think).

Which is easier for stupid blonds?

...

>HDA4: the rest/NTFS or FAT.  This will be the share drive.  

which one better, NTFS or FAT?

...

>3.  Everything but your wireless should work out of the box.

what should I do for wireless?
Bluetooth will work?[/QUOTE]

Kubuntu is pretty nice - my colleague set it up kubuntu breezy for his elderly mother who had only used windoze, and she loves it.  I'd say a 'stupid blond' should have even less problems.

The problem with NTFS is that linux support for NTFS is spotty - reading seems pretty good, but there are occasional problems with writing.  I understand that the problem with FAT has to do with large disks, but I don't know the details.  Frankly, I'd go all ext3, but if you want shared space between windoze and linux, I'd probably take FAT for reliability.

As for wireless, dapper now supports the 3945 wireless out of the box.  I've got it on my Dell D620, and it's shiny.
Can't say about bluetooth.

---

### Post by steel_lady on 2006-05-25
OK. Gracias!

Now only one question left: Isn't it better to put double swap?

---

### Post by nolongerlivecd on 2006-05-25
I too have 1GB RAM, but I don't use swap...

---

### Post by charles.figura on 2006-05-25
[QUOTE=steel_lady]OK. Gracias!

Now only one question left: Isn't it better to put double swap?[/QUOTE]
My D620 has 2GB ram and an 80GB disk.  Ubuntu autoconfigured 3GB of swap.  That's a lot, but I'm running some really high-intensive memory applications as part of my research.  What kind of apps are you running?  That's as good a tell as anything.  1GB is probably plenty for most applications.

---

### Post by steel_lady on 2006-05-25
[QUOTE=charles.figura]My D620 has 2GB ram and an 80GB disk.  Ubuntu autoconfigured 3GB of swap.  That's a lot, but I'm running some really high-intensive memory applications as part of my research.  What kind of apps are you running?  That's as good a tell as anything.  1GB is probably plenty for most applications.[/QUOTE]

I intend to process huge astronomical images

---

### Post by charles.figura on 2006-05-25
[QUOTE=steel_lady]I intend to process huge astronomical images[/QUOTE]
Well, given that I'm doing astrometric analysis (image analysis and orbital analysis/solutions, I might recommend a bit more swap.  Of course, the real computer gurus might think that's crazy, but what the hey.

Not like you were going to use the extra gig of disk anyway.

---

### Post by steel_lady on 2006-05-25
[QUOTE=charles.figura]Well, given that I'm doing astrometric analysis (image analysis and orbital analysis/solutions, I might recommend a bit more swap.  Of course, the real computer gurus might think that's crazy, but what the hey.

Not like you were going to use the extra gig of disk anyway.[/QUOTE]

yes, true...

---

