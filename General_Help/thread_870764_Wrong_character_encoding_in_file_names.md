---
title: "Wrong character encoding in file names"
date: 2008-07-26
forum: General Help
---

### Post by chattanoga on 2008-07-26
I have a folder that is shared between Ubuntu and WinXP (dual boot), containing mostly mp3s and jpeg-images. 
Previously it was placed in a separate FAT32 partition, but when installing Hardy Heron I decided to place the folder in the windows partition (NTFS).

Now all files containing ÅÄÖ have special characters instead:
example: "Höjdarnas Höjdarsånger" is called "HÃ¶jdarnas HÃ¶jdarsÃ¥nger"

I assume that the problem is related to fstab. I do not know what the fstab looked like during the Hardy period (ie when the problem probably began).
I am currently using Ubuntu 7.10 and my fstab looks like this:
/dev/sda1 /media/windows ntfs nls=utf8,umask=0, 0 0


Question 1: What happened?
Did Ubuntu assume that I wanted rename all files?

Question 2: Is there a simple way to fix the problem?

---

