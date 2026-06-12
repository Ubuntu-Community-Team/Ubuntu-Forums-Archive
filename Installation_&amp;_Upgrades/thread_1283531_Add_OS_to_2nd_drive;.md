---
title: "Add OS to 2nd drive;"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by darco on 2009-10-05
Was wondering how I would go about adding Linux to a second hdd while the first hdd already dual boots Linux/Windows? 
The first hdd is running Mint/Win with Grub2. I would like to install Karmic on the second drive by itself using Ext4. Would Grub2 pick up both drives or would I have to choose  hdd1 or hdd2 during boot up to choose which OS/Grub menu I want? 

I have read some post regarding dual booting w/two drives but that was Win and Linux so not sure how two Grub2's would work.
Uggh, I hope Grub2 editing is not needed..not up for that just yet.

thxs

darco

---

### Post by SuperSonic4 on 2009-10-05
I'd remove the first hdd and install karmic on the second.

After that plug the first back in, boot into the first one and edit mint's menu.list (assuming it's grub 1.5) to include karmic.

Alternatively the BIOS could do the same thing just pick a drive to boot onto with each boot up

---

