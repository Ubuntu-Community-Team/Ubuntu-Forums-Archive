---
title: "Trying to fix &quot;Lost+Found&quot;  for newly installed HD in file browser"
date: 2010-01-20
forum: Hardware
---

### Post by fagan on 2010-01-20
When I finished allocating the newly formatted HD that am trying to install using gparted, I get a "lost+found" folder icon under 80G-File Browser. I am trying to get the system to recognize the HD and I also would like to have a folder for this drive on my desktop please advice with this also. What do I do from here? Thanks in advance.

---

### Post by fagan on 2010-01-20
What does "Lost+Found" mean exactly? that the drive is "unmounted"?

---

### Post by wojox on 2010-01-20
This should explain it: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by fagan on 2010-01-20
Okay I read the link that you posted for me and went into terminal to run sudo fsck and it only recognized 1 drive to check. That drive is the drive that Ubuntu is now loading from and it is also the HD that had all of my media on. I aborted the check because, it was for the wrong drive. The drive may not be mounted. How do I mount this HD named 80G?

---

### Post by jocko on 2010-01-20
> **fagan said:**
> Okay I read the link that you posted for me and went into terminal to run sudo fsck and it only recognized 1 drive to check. That drive is the drive that Ubuntu is now loading from and it is also the HD that had all of my media on. I aborted the check because, it was for the wrong drive. The drive may not be mounted. How do I mount this HD named 80G?

If you see the lost+found folder, the partition IS already mounted. The lost+found folder is created automatically in the root of any partition. If the partition was unmounted, you would NOT see the lost+found folder...
To see if it is mounted, type "mount" in a terminal. It should output all mounted filesystems.

---

### Post by fagan on 2010-01-20
Okay I do notice that it ts showing up as the last thing on the list. But I am not noticing my 40G HD on this list. The first thing on this list is:

/dev/sdal on / type ext3

is this my 40G HD?

The last thing on the list is:

/dev/sdb1 on /media/80G type ext2

what do I do next? And should I install nautilus?

---

### Post by jocko on 2010-01-20
> **fagan said:**
> Okay I do notice that it ts showing up as the last thing on the list. But I am not noticing my 40G HD on this list. The first thing on this list is:

/dev/sdal on / type ext3

is this my 40G HD?

The last thing on the list is:

/dev/sdb1 on /media/80G type ext2

what do I do next? And should I install nautilus?

I'm not sure what your problem is. Do next? Depends on what you are trying to accomplish. You haven't stated what problems you have. Install nautilus? Don't you already have ubuntu installed? Nautilus is ubuntu's default file browser (that's the program that shows your desktop, and which you also use to browse through the folders in your filesystems, similar to "windows explorer" if you're more familiar with windows terminology), so unless you have uninstalled it you already have it. You do see your desktop, right?

/dev/sda1 is the partition where you have ubuntu installed (/), whether or not that drive is 40Gb only you can know. You'll know for sure by running this command in a terminal:
```
sudo fdisk -l
```It will show you a list of all hard drives and removable drives you have attached at the moment, and it will also show you all partitions or unpartitioned spaces on those drives.

---

### Post by fagan on 2010-01-20
The 80G drive that I was trying to install shows up on my desktop. When I run 'mount' the drive is listed. But when I double-click on the 80G drive at my desktop it brings up the File Browser with 1 file that says, "Lost+Found". When I double-click on this folder in comes up with a window that alerts me that I "Do not have Permissions to view this folder" What do I do next?

---

### Post by jocko on 2010-01-21
> **fagan said:**
> The 80G drive that I was trying to install shows up on my desktop. When I run 'mount' the drive is listed. But when I double-click on the 80G drive at my desktop it brings up the File Browser with 1 file that says, "Lost+Found". When I double-click on this folder in comes up with a window that alerts me that I "Do not have Permissions to view this folder" What do I do next?
Next? You smile and try to be happy? The lost+found folder *is supposed* to be there. It is created automatically in the root of every partition, and does not contain any files unless a fsck has found lost or corrupted files (which I find VERY unlikely on a new partition that you haven't put any files on yet).
Why are you trying to "fix" something that isn't broken?

---

### Post by Wrapperband-0 on 2012-11-06
I've also got this problem. Basically, the previous answer missed the point.

I formatted my 500 GB 12.04 disk, partition 1 - to install 12.10 + 16 GB linux swap.

After the install I now notice i have 3 disk partitions. The first contains a directory the same size as my old 12.04 install (227GB). In Dolphin it is called (lost+found). The second in my install, 3rd is swap..

I believe I must have answered a question incorrectly in the install, and "something" has tried to recover my old 12.04 Ubuntu install.

I basically have lost half my disk and the 12.10 is on an Extended partition!

As it is newish install, I'm going to reformat the disk into ntfs first, then reformat toext4, in the hope that presents the newly formatted drive to the install I thought I did before.

---

