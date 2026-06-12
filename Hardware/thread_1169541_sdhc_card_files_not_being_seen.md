---
title: "sdhc card files not being seen"
date: 2009-05-25
forum: Hardware
---

### Post by ubuntumaybe on 2009-05-25
Hi,

I have a 16gig sdhc card and I use a usb card reader to connect it to my laptop. I am running jaunty. I successfully copied over 7 gig of various stuff to it and verified that it was there by reading it in the file manager. When I checked it on XP it was not there. Although the system is telling me that I have used 9gig with 6 gig available. Then when I looked for the files on jauty again they were not there but it tells me that I have used 9gig with 6gig free. I know the files are on the card. Is there any way I can get to view them. Thanks.

---

### Post by taurus on 2009-05-25
When you copied files to it from Ubuntu, did you remember to unmount it first before you unplugged it from your machine?

---

### Post by fishyf on 2009-05-25
> **ubuntumaybe said:**
> Hi,

I have a 16gig sdhc card and I use a usb card reader to connect it to my laptop. I am running jaunty. 

    :
    :

What was the Laptop?

It could be that the files were hidden or that permissions did not allow you to see them. Were you logged in as the same user that created the files.

Open a terminal in the directory where the card is mounted and run the du command.
Type du -h
This will tell you which files are using the 9G of disk space.

Alternately, use the Disk Usage Analzser (applications, accessories), select scan folder and choose the card mount point (probably /media/disk)

Also, can you confirm that the file system on the card is FAT? (Presumably FAT32).

---

### Post by ubuntumaybe on 2009-05-26
> **taurus said:**
> When you copied files to it from Ubuntu, did you remember to unmount it first before you unplugged it from your machine?

Hi,

I also have a 1 gig pendrive and I never unmount that before removing and I never have problems.

---

