---
title: "[SOLVED] 2GB MicroSD Card showing up as 1GB?"
date: 2008-08-14
forum: General Help
---

### Post by Gannon8 on 2008-08-14
I have a 1GB SD Card and a 2GB MicroSD card that usually stays in it's adapter. I was having a bit of problems with the 1GB SD card: Linux said it could not delete a ext3 partition while setting up the superblocks. So I deleted it in windows, and somehow it deleted the whole device :confused: but I kind of wanted that anyway so I stuck with it.

So I am using my 2GB MicroSD card to upload homebrew apps for the wii. I wanted to partition my 1GB one, but I had forgotten to stick it in. GParted showed the card as 1GB with no partitions, and since GParted prints some errors, like this one, in the terminal, nothing showed up, and I formatted it. After formatting, I looked at my SD card reader and saw my MicroSD card in it. I wondered why GParted thought it was 1GB, but It showed my IPod and Floppies in the same matter.

So here I am, with a 2GB SD card that the computer thinks is 1GB, even windows. How do I get it back to 2GB again?

---

### Post by damis648 on 2008-08-14
Try using gparted again and set the disk label (defualt to MSDOS disk label) and see if that fixes it.

---

### Post by jnw222 on 2008-08-14
similar program

if disklabel doesnt work   post the output of 
sudo fdisk -l

---

### Post by Gannon8 on 2008-08-14
Creating a new disklabel does not help.

Output of fdisk -l
```
Disk /dev/sdd: 1006 MB, 1006632960 bytes
31 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes
Disk identifier: 0x000e83ee

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by Gannon8 on 2008-08-14
Perhaps it's the manufacturers fault for preformatting it and configuring it improperly.

---

### Post by Gannon8 on 2008-08-15
Is there anyway to delete the partition table without making a new one? Maybe that will help.

---

### Post by Gannon8 on 2008-08-15
> **jnw222 said:**
> similar program

if disklabel doesnt work   post the output of 
sudo fdisk -l

So did you get it fixed? Testdisk has a function for selecting sector count and stuff like that. Maybe I could use that?

---

### Post by Gannon8 on 2008-08-15
I see the problem now. I tried plugging it in to my mom's sd card reader, which has a native MicroSD card slot, so I don't need an adapter, and gparted views it as a 2GB one finally. I am guessing my dad's reader was so old it didn't recognize cards over 1GB. Meh, so I have it fixed.

---

