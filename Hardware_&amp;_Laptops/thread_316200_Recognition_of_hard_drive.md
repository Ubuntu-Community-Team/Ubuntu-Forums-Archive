---
title: "Recognition of hard drive"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by brdmartin on 2006-12-10
I just purchased a new 250 gb hard drive, as my original 40 gb is overwhelmed due to dual boot w/ windows, and lots of mp3s and raw photo files. I chose to place the new drive as a slave, as I have no way to reinstall windows. The drive came with some software to help windows set the drive up, and I was hoping that when I started Ubuntu, the new drive would be just sitting there ready, but not so lucky. 

Ok, so my question is, from the perspective of a total noob, how do I get this drive going in Ubuntu? The box says it's a EIDE hard drive. any help appreciated. :)

---

### Post by spd106 on 2006-12-10
Hi, you need to create a partition and then format it with a file system in order to store files. While you could use terminal tools like fdisk, I suggest that you install gparted since it has a nice gui and will be vaguely familiar as it is used in the ubuntu desktop installer. It can be found in synaptic and add/remove programs.

How many partitions you want and which file system are up to you though I suggest you stick with the default ext3 file system.

---

### Post by brdmartin on 2006-12-13
Here is what I was hoping for though... to be able to access the files on it with both Ubuntu and windows. When everything was under my 40gb hard drive, I was able to access all my windows files when in Ubuntu. For instance, this allowed me to listen to the same mp3s the mater what system I had loaded, and I could work with the same photo file with GIMP and Corel Paint Shop. 

Is there any way to have Ubuntu recognize the second hard drive, without having to partition it and format that section specifically for Linux?

---

### Post by Wim Sturkenboom on 2006-12-13
You do not need a Linux specific format on the disk.

Do you want to be able to _write_ to that disk from within Linux? If so, you need to format as FAT32. If you only want to read from it, you can format as NTFS.
In the first case (FAT32) you indeed need a partition tool or do it from commandline. Problem is that Windows can not create FAT32 partitions greater than 32GB (Linux can), so you are forced to use 3rd party stuff.
In the second case you can simply format the HD in Windows. Make sure that your version of Windows supports the big size (for WinXP, you need SP2).

There is a program/driver for windows that allows you to read/write ext2. Just search. In that case you (obviously) have a third choice.

---

