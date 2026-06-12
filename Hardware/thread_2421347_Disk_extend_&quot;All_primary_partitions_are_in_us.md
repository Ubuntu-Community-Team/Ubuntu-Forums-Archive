---
title: "Disk extend &quot;All primary partitions are in use.&quot; error"
date: 2019-06-20
forum: Hardware
---

### Post by denizguzel on 2019-06-20
Hi, I have an error about disk resize. I extended the ubuntu disk four times on VMWare data centre. After I did it as fifth. But I can't extend. I am taking "All primary partitions are in use." error with cfdisk. How can I do this? In the beginning, I didn't know. How can I use this size?

---

### Post by yancek on 2019-06-20
Is this a Legacy/MBR install?  If you are using GPT you can have up to 128 primary partitions.  If you are using Legacy/MBR you can have only four primary partitions one of which can be an Extended partition and within the EXtended you can create Logical partitions.  Run cfdisk or fdisk -l and post the output here.

---

### Post by denizguzel on 2019-06-20
screenshot is below.
[ATTACH=CONFIG]283459[/ATTACH]

---

### Post by TheFu on 2019-06-20
Cannot read the image. Sorry.

This issue isn't Linux. It is a limitation from MS-DOS partitioning left over from the early 1980s.
With virtualization, you could just add a 2nd virtual disk and mount it into the guest, move all the data over with larger-sized partitions or take the 3rd-4th partitions an move those to a new virtual disk and leave the others on the first virtual disk, expanding the 2nd partition into were the 3rd and 4th partitions were previously.  This assumes the underlying physical hardware being used by the VMhost has more storage available, of course.

Please copy/paste the text and put into **code tags** so people with eyesight issues might help and bandwidth isn't wasted for people who pay by the byte for their internet.  Adv-Reply (#) [Go Advanced or Advanced Edit] is how to access the code tags button. You can manually enter the tags too.  The output from the terminal should line up exactly the same when posted here. If it doesn't, then you didn't get the code-tags correct.

More advanced users would choose LVM for the installation, so extending LVs is prety easy later.  LVM provides all sorts of advanced file system and storage capabilities not available otherwise. The price is more complexity.  Also, it works best with ext4 file systems, since LVM knows how to expand those at the same time the LV is expanded to use more VG storage.  There are lots of LVM How-To guides on the internet.  LVM on all Linuxes is the same. Same commands, so there isn't a need to find an Ubuntu-specific guide.

---

### Post by oldfred on 2019-06-20
Please post terminal output and use code tags to preserve formatting. Do not use screen shots except for gui output, but normally terminal output gives more info.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) 
    
I can barely make out your screen shot, but it looks like you are using LVM.

---

### Post by TheFu on 2019-06-20
If using LVM, then the output from these commands is needed:
```
lsblk
sudo lvs
sudo vgs
sudo pvs
```

There might be lots we can do. I can't read the image. Doesn't look like any output I've seen before.

---

### Post by Dennis N on 2019-06-20
Since sda3 is the last partition on the drive, you could resize it with gparted into the 200 GB unallocated space immediately following to make use of that space. Needs to be unmounted when operating on this. My LVM notes say use pvresize after this to have the pv size fill a resized partition - but maybe not(?) - in a quick test, gparted resized the pv as well (which I didn't expect) by adding more extents. The vg that included the pv also grew to reflect the change. At least that's what pvs and vgs showed before and after.

---

### Post by TheFu on 2019-06-20
Actually, no need to resize the pv.  Just add another volume through VMware, put it into a separate PV inside the guestOS, then add it to the existing VG and extend any LV you like using lvextend with the --resizefs option to handle the file system at the same time. If the virtual disks used for the PV are on the same physical VMware volume, there isn't much risk and doing it this way. It will be the quickest, easiest, way.  This is one of the reasons LVM totally ROCKS!

---

### Post by denizguzel on 2019-06-21
The results you want are below.

> root@:~# lsblk                                                                                                                                       
NAME                   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
fd0                      2:0    1     4K  0 disk 
sda                      8:0    0   564G  0 disk 
&#9500;&#9472;sda1                   8:1    0   487M  0 part /boot
&#9500;&#9472;sda2                   8:2    0     1K  0 part 
&#9500;&#9472;sda3                   8:3    0   100G  0 part 
&#9474; &#9492;&#9472;ubdev01--vg-root   252:0    0 767.5G  0 lvm  /
&#9500;&#9472;sda4                   8:4    0   200G  0 part 
&#9474; &#9492;&#9472;ubdev01--vg-root   252:0    0 767.5G  0 lvm  /
&#9492;&#9472;sda5                   8:5    0  63.5G  0 part 
  &#9500;&#9472;ubdev01--vg-root   252:0    0 767.5G  0 lvm  /
  &#9492;&#9472;ubdev01--vg-swap_1 252:1    0  1020M  0 lvm  [SWAP]
sdb                      8:16   0   200G  0 disk 
&#9492;&#9472;sdb1                   8:17   0   200G  0 part 
  &#9492;&#9472;ubdev01--vg-root   252:0    0 767.5G  0 lvm  /
sdc                      8:32   0   205G  0 disk 
&#9492;&#9472;sdc1                   8:33   0   205G  0 part 
  &#9492;&#9472;ubdev01--vg-root   252:0    0 767.5G  0 lvm  /
sr0                     11:0    1  1024M  0 rom  
> root@:~# lvs
  LV     VG         Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubdev01-vg -wi-ao----  767.51g                                                    
  swap_1 ubdev01-vg -wi-ao---- 1020.00m 
> root@:~# vgs
  VG         #PV #LV #SN Attr   VSize   VFree
  ubdev01-vg   5   2   0 wz--n- 768.51g    0 
> root@:~# pvs
  PV         VG         Fmt  Attr PSize   PFree
  /dev/sda3  ubdev01-vg lvm2 a--  100.00g    0 
  /dev/sda4  ubdev01-vg lvm2 a--  200.00g    0 
  /dev/sda5  ubdev01-vg lvm2 a--   63.52g    0 
  /dev/sdb1  ubdev01-vg lvm2 a--  200.00g    0 
  /dev/sdc1  ubdev01-vg lvm2 a--  205.00g    0

---

### Post by TheFu on 2019-06-21
**Please edit the post above for CODE TAGS**!!!  Can't read it without the proper indentation.
[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168) explains.

---

