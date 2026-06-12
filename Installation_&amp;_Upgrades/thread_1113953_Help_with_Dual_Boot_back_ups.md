---
title: "Help with Dual Boot back ups"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by kacike76 on 2009-04-02
HI all, 

I have a dv7-1025nr HP pavilion laptop that I need to send for service (something related to the screen).  Before doing so, I need to make sure I back up my entire hard drive.  I have a dual boot hard drive with Vista x64 and Ubuntu 8.10 x64.  I was looking at using acronis true image home 2009 for the job of creating an entire image of the hard drive with both partitions that I can restore if HP decides to give me a new laptop.  I would then write this image to my Netgear ReadyNAS duo, and restore it if needed.  I bought acronis yesterday, but after reading some reviews online, I am not sure I’ll work.  
So, does anyone have any experience creating images of entire harddrives for dual boot systems? And how do I know it worked after I create the image? I would hate to create an image and get a new laptop (identical hardware) and find that I lost my ubuntu partition.  

Please help
Thank you

---

### Post by dandnsmith on 2009-04-02
You need to be a bit careful about how you do the backup.
Acronis has quite detailed help, and you need to avoid the situation where you image the whole HDD, as recovering it to a 'new' HDD will make the new a chinese copy of the old - not the best idea if the HDDs differ at all in specification (size and layout of the tracks ...)

I backup each partition (for my multiboot systems), and ensure that I have enough information about the partitions to be able to set up the new HDD in basic fashion before the restore (this includes how the booting is carried out).

Acronis can do things like expand the partitions automatically to fill the space available, but I've had the odd 'funny' which convinces me to be careful, and do one step at a time.

---

### Post by kacike76 on 2009-04-02
Thank you.  I guess i am not very familiar with the restore procedure, but say i get a new HDD.  Given i have all the information about the existent HDD (size..i am not sure what else i need), i would partition the new drive in the same way.  Once that's done how do i restore Ubuntu and Windows separately if i choose to go with your suggestion of not creating an image of the whole HDD.

---

### Post by dandnsmith on 2009-04-03
My memory (somewhat suspect these days) says that you don't need to do the partitioning - that the Acronis restore can operate into free space on the new disk.

Further, you can select any or all of the partitions when doing the restore (if you've backed up multiple partitions at one time). The thing you have to watch for is making the new disk bootable when you've finished - this is where you need to be aware of how the boot process you want to use operates, and how it was set up. The Acronis backup gives hints about the boot partition and so forth - it is best to have at least a dummy run to see how the dialogues go.

---

