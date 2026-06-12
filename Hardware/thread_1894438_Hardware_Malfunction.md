---
title: "Hardware Malfunction"
date: 2011-12-12
forum: Hardware
---

### Post by GeneralBrae on 2011-12-12
Hi there
 
I am running Ubuntu alongside Windows 7 on my HP laptop. I have an external hard drive (Toshiba) that has run fine for over a year on Windows. I have used it a bit on Linux and now when I try to run it on Windows again it isn't recognised by the OS. However it still runs fine on Ubuntu. Nothing at all appears when I plug it in but power is getting to the hard drive. Any help on how to get this working on Windows again would be appreciated.
 
The same is also true of a 3 mobile broadband dongle I have had for some time. Again any help would be appreciated.
 
Finally, I am a Ubuntu noob so please use small words ;)

---

### Post by Dlambert on 2011-12-12
> **GeneralBrae said:**
> Hi there
 
I am running Ubuntu alongside Windows 7 on my HP laptop. I have an external hard drive (Toshiba) that has run fine for over a year on Windows. I have used it a bit on Linux and now when I try to run it on Windows again it isn't recognised by the OS. However it still runs fine on Ubuntu. Nothing at all appears when I plug it in but power is getting to the hard drive. Any help on how to get this working on Windows again would be appreciated.
 
The same is also true of a 3 mobile broadband dongle I have had for some time. Again any help would be appreciated.
 
Finally, I am a Ubuntu noob so please use small words ;)

You might have it formatted to a LINUX only format such as ext4 or ext3 etc, Open up unity's dash and type "disk" and select disk utility, then find out the format or your drive. 

You may need to format or download a program to read Linux drives in windows.

---

### Post by utnubuuser on 2011-12-12
read/write linux formats in Windoze...  [http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html]("http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html")

---

### Post by Dlambert on 2011-12-12
> **utnubuuser said:**
> read/write linux formats in Windoze...  [http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

Thank you, I didn't look.

---

### Post by Mark Phelps on 2011-12-14
If you didn't reformat it, and it's still formatted FAT or NTFS, did you simply just unplug the drive from Ubuntu -- instead of safely removing it?  IF it is NTFS, that can leave the partition in a bad state, presenting problems later.

When you are in Win7, I take it that when you plug in the drive, there is no indication of it beeing seen, right?

In that case, open Win7 Disk Management and scroll down through the list.  The drive may actually be listed but not mounted.  IF it is, see if there is an option to assign it a drive letter.  If there is, do that -- and the drive should then mount.

If you contine to have problems seeing the drive under Win7, you would do better going to the Win7 forums (sevenforums.com) and asking about it there -- for a Win7-based solution.

---

