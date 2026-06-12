---
title: "Install-Partitioning Problems"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by jyper on 2008-12-13
Can anyone help?
Atempting to install Xubuntu 8.10 32 bit
on an older laptop w/ ~50 GB hard drive that I think is one big NTFS partition

When I get to the partitioning screen no partitions are shown.

(Also strangely my windows parttion apears to be automounted under /cdrom

---

### Post by Pumalite on 2008-12-13
How much memory do you have?
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by jyper on 2008-12-13
1/2 GB ram
The livecd is very responsive, its just when you get to the partitioning stage it doesn't show any partitions.

---

### Post by taurus on 2008-12-13
Open a terminal from the LiveCD and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jyper on 2008-12-13
1.
      ubuntu@ubuntu:~$ sudo fdisk -l
   2.
       
   3.
      Disk /dev/sda: 60.0 GB, 60011642880 bytes
   4.
      255 heads, 63 sectors/track, 7296 cylinders
   5.
      Units = cylinders of 16065 * 512 = 8225280 bytes
   6.
      Disk identifier: 0x94e494e4
   7.
       
   8.
         Device Boot      Start         End      Blocks   Id  System
   9.
      /dev/sda1   *           1        7295    58597056    7  HPFS/NTFS
  10.
      ubuntu@ubuntu:~$

---

### Post by taurus on 2008-12-13
Is there anything on /dev/sda1?  If you plan to use the whole harddrive to install Xubuntu, you could use gparted from the LiveCD and format it to ext3.  Now, see if the installer detects the harddrive this time.

---

### Post by jyper on 2008-12-13
A windows installation is on it.
A plan on Dual-booting in case the person I'm installing it for doesn't like Ubuntu, but like I said partioner isn't working, even to show mounted drives and I don't know how to unmount it.

---

### Post by taurus on 2008-12-13
First, boot into windows and run a defrag of the harddrive a couple of times.  Then, boot with the LiveCD and see if it works this time.

Another option is the wubi if you are not sure whether he likes Ubuntu or not.

[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)

---

### Post by Pumalite on 2008-12-13
Try Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it
(it works with unmounted drives/partitions)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

