---
title: "Seagate 2TB External HDD Gone RAW"
date: 2011-06-28
forum: Hardware
---

### Post by PcPro12 on 2011-06-28
Alright, so I've spent nearly a week trying to solve this problem with almost no success. I need some third party input before I continue with my plans for this drive. So here's the story.

I have a Seagate FreeAgent 2TB external hard drive, I filled it about halfway with data, important data, which I REALLY need to save. No joke. The external was on the ground and someone accidentally stepped on the usb cord, which broke the input into the external. Having already broken one like this before, I did what I did before. I took the HDD out and hooked it to the computer, the problem was that it showed up as RAW format. It worked fine, now it's RAW and asking me to reformat. So I spent several days using Photorec to recover the files, which barley recovered anything. I tried several other programs to no avail. Once it asked me to reinitialize the HDD, probably my biggest mistake, as after doing that in windows the drive shows up as "Unallocated Space" and I can't used tools such as Redcuva or NTFS Undelete to recover it, because I can't select the HDD and in linux it says it doesn't support the GUID File System.

I really need to save this data on the external and I was thinking of creating an NTFS partition on the external and trying to use RECUVA or NTFS Undelete to try to recover the data, or even iCare Data Recovery or EASEUS Data Recovery.

Anyone got any input on this? What's the best course of action to ensure I can successfully recover all my data? Any other way to use linux to repair the NTFS partition or even write an NTFS file system without damaging the files?

Thanks,
PcPro12

---

### Post by oldfred on 2011-06-29
Raw means it has lost the NTFS signature in the partition boot sector or PBR.

If the backup is ok then this will work. (NTFS has a backup of the boot sector). this was for those who wrote grub into the PBR overwriting the windows PBR. But recovery is just the same.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If not a windows fixboot or possibly using testdisk to rewrite a new PBR may work. But try the recovery of the backup with testdisk first.

---

### Post by doas777 on 2011-06-29
+1 for testdisk, but be sure to recover the files to a different drive so you don;t overwrite unrecovered files with recovered ones.

be very careful with the disk. if you think it might be mechanically damaged or are worried about destroying data while trying to fix the partition, taking an image of it with ddrescue should ensure that even if fixing your partition metadata goes horribly awry, you have the image to fall back on.

good luck.

---

### Post by mastablasta on 2011-06-29
> **oldfred said:**
> Raw means it has lost the NTFS signature in the partition boot sector or PBR.
 

 
I think partition doctor shoudl also be able to recover it.

---

