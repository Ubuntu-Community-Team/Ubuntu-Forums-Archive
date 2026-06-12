---
title: "accidentally formatted external hard desk ext4"
date: 2011-02-13
forum: Hardware
---

### Post by acidrock on 2011-02-13
is there a way i can restore my files back after formatting, I think original format was NTFS and i formatted it to EXT4

it is 500GB external HD

---

### Post by vanadium on 2011-02-13
Format the disk again, and place the files back from your backup. It is not possible to "undo" your formatting. If you do not have a backup, you could try recover files using testdisk, but it will not be an easy process, and you will not recover everything.

Testdisk is aimed at recovering partitions that have gone astray because of faulty software, virusses, etc. However, I don't know how well it will work if you already formatted the partition again.

---

### Post by Hawkoon on 2011-02-13
In the absence of any backups it is definitely worth trying to recover (at least some) data with testdisk or foremost. It certainly worked for me and I found out that formating an XD card was not enough to prevent someone from restoring old photos on it.

So don't do anything to the drive but first take an image of the whole drive with dd
 
 ```
dd if=/dev/xxx of=/path/to/image
``` where you replace xxx with the device node of your formated drive (use fdisk to find out the device node). You will also need at least 500GB free space for storing the image file, and another 500GB for the restored data, this can be on a separate partition though.

After taking the image, disconnect your formated drive to make sure you don't accidentally write data on it.
 
 Now you can carve the image for known files. I have used both foremost and photorec. They don't necessarily produce the same results, so it is worthwhile trying both.
 
 You will have to install foremost, and for photorec you will have to install testdisk. You run both apps from the terminal. In photorec I used advanced options and selected the smallest block size, which restored more files than using larger block sizes.

If you need more help on this method let us know.

---

### Post by acidrock on 2011-02-13
i tried photorec last night before i go to sleep,i have selected the largest block "entire hard desk" when i woke up i got the message that my internal HD is out of space and i was happy that i recovered some of the files, but then i checked them and they all were text files and some JPEG but not AVI.

i could not recover all of the pictures though..

is there a software i hook-up the external HD to windows and try a software like file recover or something

also i found this tool [http://www.stellarinfo.com/linux-data-recovery.htm]("http://www.stellarinfo.com/linux-data-recovery.htm")

not sure if it would work.

---

### Post by Hawkoon on 2011-02-13
> **acidrock said:**
> i tried photorec last night before i go to sleep,i have selected the largest block "entire hard desk" when i woke up i got the message that my internal HD is out of space and i was happy that i recovered some of the files, but then i checked them and they all were text files and some JPEG but not AVI.

So you need a larger target drive then.

And try to run photorec with different block sizes. On my FAT32 memory cards 512 worked the best.

---

### Post by mr_luksom on 2011-02-13
Also, you can select which types of files to recover with photorec-  if there are too many txt files, just reselect before rerunning. I recovered all of my photos doing this after an accidental reformat.

---

