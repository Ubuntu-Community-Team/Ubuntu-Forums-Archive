---
title: "External hard drive"
date: 2013-07-05
forum: Hardware
---

### Post by progra on 2013-07-05
Hi i have a problem to mount my external hard drive on ubuntu but it work perfectly on windows hi mounting automatically.  Can you help me to solve this problem.

[http://hpics.li/4107fa3](http://hpics.li/4107fa3)

---

### Post by sudodus on 2013-07-05
Welcome to the Ubuntu Forums :-)

Start the file browser, sometimes found as an icon named Home.

In the left panel of the file browser, you should see icons for the partitions, that are available, and one of them should be the one of your external drive. Normally it should auto-mount, when you click on that icon, and you will see its folders and files in the main window of the file browser.
 
But the name that is displayed might not be the same as in Windows. That can be fixed, if you set a ***label*** for that partition. (You can set the label in Windows as well as in linux, and then it will be seen as that label by both operating systems. You can use some own name, that is easy to rememeber, for example data, pictures, video, backup ... It is convenient to set labels with ***gparted*** in linux (but avoid other operations unless necessary, because the other things are dangerous and can destroy your data unless you know exactly what you are doing).

---

### Post by sudodus on 2013-07-05
If there is a partition and data on the drive, which can be seen by Windows, but not Ubuntu it can be for a few reasons

1. Dynamic partitions: Windows dynamic partitions can not be managed by linux. If you want to share the data, you must have standard partitions.

2. Some error in the partition table, that happens to work with Windows but not linux.

3. Hardware or firmware in the casing for the external drive, that does not work with linux (no suitable drive found),

---

### Post by progra on 2013-07-05
and what is the solution???

---

### Post by sudodus on 2013-07-05
It depends on the problem. Start by checking in Windows, if it is a dynamic partition.

---

### Post by progra on 2013-07-05
the problem is when i want to format in on fat32 it always ntfs!!!!

---

### Post by sudodus on 2013-07-05
I think you can format a partition in Windows and in linux (for example with gparted). And it is possible to select file system. Use the tool, that is easier for you to use.

Why do you want fat32 (and not ntfs)?

Anyway, it is possible to do it in gparted, select either of the file systems available. Gparted comes with the iso file, so you can run it in a live session from the Ubuntu install drive.

FAT32 is older, simpler and faster. NTFS is more secure, because it has journaling. Another difference is that the max file size in FAT32 is 4 GB, which there is no practical limit in NTFS (except the partition size).

---

### Post by progra on 2013-07-05
:( i already tried the gparted sometimes its mounting and something not but now it never mounting

---

### Post by sudodus on 2013-07-06
- Do you have valuable data on the external drive?

- Can you still read those data from Windows?

- But you cannot read the drive from Ubuntu?

Then I suggest that you should be very careful and not try too much with anything that might destroy your data.

If you want to use it in Ubuntu (or any linux distro) you should check in Windows if it has dynamic partitions, because such partitions do not work with linux. Browse the internet and read about windows dynamic partitions!

You should also check if it is some special kind of external drive or casing, that needs special drivers to work. In some cases there are no suitable drivers for linux. Post the brand name and model of your external drive, and maybe someone else will recognize it and give you tips. (You can also browse the internet for linux and that brand name and model of your external drive.)

---

### Post by Mark Phelps on 2013-07-06
Your screenshot shows you were trying to erase a partition on that drive, not just mount it.

It also obscures the detail information on that partition.

You really need to try connecting the drive in Windows -- and reporting back what you see, and what it does.

---

### Post by progra on 2013-07-06
Mark helps than kyou for your request, just i told you before it work perfectly on windows but not in linux, in the beginning when i bought it , it was working correctly on linux but suudenly the problem that i show you on the pictur happened, i was thinking that the external was destroyed but when i tested in windows it work,, why i don't know???

---

### Post by progra on 2013-07-08
so i what kind of partition i should install the primary partition or extended????

---

