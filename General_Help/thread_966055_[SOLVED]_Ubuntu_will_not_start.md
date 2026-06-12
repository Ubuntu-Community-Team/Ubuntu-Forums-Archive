---
title: "[SOLVED] Ubuntu will not start"
date: 2008-11-01
forum: General Help
---

### Post by AndreLeComte on 2008-11-01
I am very new to Ubuntu and somehow I have lost the ability to start the operating system. When I boot from the Ubuntu CD both hard drives are listed but only the files from Windows Vista are accessible.
Any advice please?

---

### Post by eaidoido on 2008-11-01
are you talking about the boot screen? for example, when you turn on the computer, you only see an option to boot into Vista? its possible your grub menu.lst file doesnt include an Ubuntu option

---

### Post by AndreLeComte on 2008-11-01
The computer boots straight to Vista without a boot screen.
I think the grub menu.lst file does not exist?

---

### Post by AndreLeComte on 2008-11-01
Vista is installed on the C: hard drive and there was a folder D:\ubuntu
Does that folder need to be restored? Is it possible to restore it?

---

### Post by rhcm123 on 2008-11-01
if your disk drive was :d, then it installed to another hard drive that vista didn't notice
wubi typically creates a separate virtual partition to instlall the os on the main hard drive
are you sure you did that?

---

### Post by AndreLeComte on 2008-11-01
Ubuntu installed on D: and I think it is in a seperate partition. Now I can only boot to Vista which is installed on C:

---

### Post by AndreLeComte on 2008-11-02
Should there be an EXT3 partition on D:? I can not find it using the Ext2 Installable File System software.

---

### Post by Yownanymous on 2008-11-02
Hmm... My Windows Vista is on C: and Ubuntu is on D: and nothing's wrong at my end.

---

### Post by AndreLeComte on 2008-11-02
Ubuntu was working fine. The problems occurred after setting up VirtualBox, or perhaps I deleted something important?

---

### Post by AndreLeComte on 2008-11-02
Should I expect to see an EXT3 system using fdisk?

> **AndreLeComte said:**
> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80af76f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   195809279    97903616    7  HPFS/NTFS

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2960a785

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   195809279    97903616    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


---

### Post by AndreLeComte on 2008-11-02
I installed Ubuntu via Wubi. Now I can not locate my personal files. If I uninstall it will they be permanently erased?
When trying to install grub, the following command does not work:
find /boot/grub/stage1

---

### Post by AndreLeComte on 2008-11-02
Did Wubi create a virtual disk file? Is there any way to restore it?

---

### Post by AndreLeComte on 2008-11-02
Is this the virtual disk?:

[IMG]http://i269.photobucket.com/albums/jj46/andrelecomte6/wubi.jpg[/IMG]

Is it possible to get access to it?

---

### Post by ago on 2008-11-03
Wubi virtual disk is c:\ubuntu\disks\root.disk
You can normally access it from any linux distro by mounting that file with the option "-o loop".

If the machine has been shut down unproperly you have to run chkdsk /r, and sometimes look for a hidden folder called c:/found.000

---

### Post by AndreLeComte on 2008-11-03
The ubuntu folder is missing. I tried chkdsk /r and there is no hidden folder named found.000
Would it be possible to mount the virtual disk using this file?:
D:\.Trash-0\files\ubuntu\disks\.fuse_hidden0000000400000003

[IMG]http://i269.photobucket.com/albums/jj46/andrelecomte6/wubi.jpg[/IMG]

---

### Post by ago on 2008-11-03
Did you use to be able to boot into Ubuntu?

---

### Post by AndreLeComte on 2008-11-03
Yes, Ubuntu was working fine but now I have lost it and all my personal files.

---

### Post by AndreLeComte on 2008-11-03
Apparently... "The trash applet that Ubuntu uses isn't compatible with FAT or NTFS formats, so when you delete something from a storage of that format, it goes to a hidden folder-namely, .Trash-name_of_drive."
Is there some way to reverse this?

---

### Post by AndreLeComte on 2008-11-03
If the ubuntu folder was deleted in Windows it would be in the Windows Recycle Bin.
However it is now a hidden folder supposedly created by Ubuntu:

D:\.Trash-0\files\ubuntu

From what I understand, I need to restore the virtual disk file 'root.disk' from the ubuntu\disks folder.
However only two files are in the folder:

.fuse_hidden0000000400000003
.fuse_hidden0000000600000004

one is 27GB and the other is 953MB
Is it possible to mount these to access my data?

---

### Post by AndreLeComte on 2008-11-04
1) In Windows I backed up the file D:\.Trash-0\files\ubuntu\disks\.fuse_hidden0000000400000003 to C:\ubuntu\disks\root.disk

2) Shutdown and loaded Ubuntu from the Ubuntu installation CD

3) Mounted the root.disk file using the following command in Terminal:
sudo mount -f -o loop /media/disk-1/ubuntu/disks/root.disk /mnt

4) Backed up all important data out of the /mnt/home folder 

5) Now I will reinstall Ubuntu

6) Problem solved, thanks for all the help :D

---

