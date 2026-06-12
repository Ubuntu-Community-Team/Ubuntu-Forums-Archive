---
title: "moving disks around"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by bob k on 2005-08-12
I have Ubuntu on hda and hdc, hdb has suffered several disk errors in the past month. I am going to by a new hard disk to replace my failing drive, and plan to move it to (0,0) in the chain.

Since all os's are on different drives can I just adjust Grub to reflect the disk drive change and install windows 
on the new (0,0) drive.

The only reason I want to install windows is I have drive image and have tested it with Linux, I keep this machine isolated from the rest of my network for google searches and web surfing.

Since this is my second time installing this month an image backup is worth it's weight in gold.

Tia

Bob

---

### Post by nad on 2005-08-13
This depends on where you currently have grub installed. Individual boot sectors or mbr? Do you boot from a bios disk pointer or grub menu?

And why not use partimage, [http://www.partimage.org/](http://www.partimage.org/) ?

---

### Post by bob k on 2005-08-14
I'm using Grub so the partimage software is going to work for me.

Thanks for the info

Bob

---

