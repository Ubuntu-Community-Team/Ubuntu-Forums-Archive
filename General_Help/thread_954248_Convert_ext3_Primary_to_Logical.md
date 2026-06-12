---
title: "Convert ext3 Primary to Logical"
date: 2008-10-21
forum: General Help
---

### Post by Vantrax on 2008-10-21
Im working with a dual boot windows/ubuntu image for some lab environments. The previous techs left the root partition outside the extended causing no end of problems.

I've been trying to use gparted to convert the ext3 / partition from a primary to a logical partition with little luck. Ive been booting off the live CD and disabling the swap allowing me to edit the extended, but I cannot find an option to move the primary into the extended.

Any ideas?

For reference the drive looks like:

[WindowsXP][Windows Scratch][Unformatted][Ext3 /][Extended(swap, etc, mentor)][Unformatted]

(couldn't work out how to upload an image)

Also anyone have a better tool to deploy dual boot images than ghost?

---

### Post by prshah on 2008-10-21
> **Vantrax said:**
> 
I've been trying to use gparted to convert the ext3 / partition from a primary to a logical partition with little luck.

Also anyone have a better tool to deploy dual boot images than ghost?

You cannot "convert" a primary partition to a "logical partition/drive". That said, you can create a logical partition in the extended partition (make the space first), then "dd" copy the entire contents of the primary partition to the logical. 

Remember to change the UUIDs in /etc/fstab (of the new/logical partition) and make changes to GRUB (from the live CD), and run update-grub. You may need to re-install GRUB; use the GRUB Super Disk (Super GRUB disk?).

As for better tool than ghost to backup/restore images, see [[SOLVED] Exact duplicate of entire HDD ]("http://ubuntuforums.org/showthread.php?t=874643")

---

### Post by Vantrax on 2008-10-21
Thanks for the hint, i guess ill have to do it that way, seems slightly redundant not to be able to do a conversion tho.

> **prshah said:**
> 
As for better tool than ghost to backup/restore images, see [[SOLVED] Exact duplicate of entire HDD ]("http://ubuntuforums.org/showthread.php?t=874643")

As for this, its great in theory if your doing a disk to disk, but if you need to transfer files to 30odd pcs at the same time this wont work too well. Ghost works somewhat with linux but tends to wreak grub and a few other bits. However its the only networked imaging tool im aware of that will do linux.

---

### Post by prshah on 2008-10-21
> **Vantrax said:**
> 
As for this, its great in theory if your doing a disk to disk, but if you need to transfer files to 30odd pcs at the same time this wont work too well. 

It _will_ work well even in that case! Replace the "of" (output file) with a filename to create an image. When restoring that image, use the filename created as an "if" (input file).

You can also compress it separately if you like, and (i'm not sure about this) you could even pipe it through tar for on-the-fly compress/decompress.

---

### Post by Vantrax on 2008-10-22
So, ive manage to extend the extended partition, create a new logical partition inside the extended and dd sda3 to sda8.

Ive updated grub, and updated fstab.

Here is when the fun starts, it boots, finds grub, then drops out to a initramfs shell with an error:

/bin/sh can't access tty; job control turned off.

Update:
Grub wasn't configured quite right, if you do see this error odds are your grub needs to be configured so it can see the right drive, make sure your root location isn't listed as a UUID. Should look like /dev/sda# (# being your drive value).

---

