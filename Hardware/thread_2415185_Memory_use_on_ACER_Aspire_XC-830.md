---
title: "Memory use on ACER Aspire XC-830"
date: 2019-03-22
forum: Hardware
---

### Post by Trevor Jones on 2019-03-22
I have just bought an ACER aspire and installed Ubuntu 18.10 alongside the Windows 10 that was preinstalled. 
When I check the memory it shows three separate memory locations:

"Computer" 407.8GB/489.3GB available  /           Ubuntu has installed itself here.
"Acer" 88.9GB/126.8  available /dev/nvme0n1p3   Widows is installed here.
"DATA" 501.3GB/ 501.4 available /dev/sda1         This has two folders $RECYCLE.BIN and System Volume Information

Can anyone advise me on the most efficient usage of these locations? I only rarely resort to windows, The main O/S I use is Ubuntu.

---

### Post by TheFu on 2019-03-22
Those are storage, not memory.

I don't understand the rest of the question. "most efficient usage" could mean all sorts of things.

The output from a few commands would be helpful.```

df -Th
inxi -D
lsblk
```
Please post with _code tags_, like I've done above, so it is readable.

---

### Post by Trevor Jones on 2019-03-23
OK TheFu forgive an old man not conforming to  your usage:
In plain language I want to know where best to put my home folder, where to store large chunks of data, is there a safe area to use for a backup? etc.
The output you requested is here, I don't know how to put it in the little panels so here is is:

df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.8G     0  3.8G   0% /dev
tmpfs          tmpfs     779M  1.9M  777M   1% /run
/dev/sda3      ext4      456G   53G  380G  13% /
tmpfs          tmpfs     3.9G   20M  3.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop1     squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/238
/dev/loop3     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop2     squashfs   43M   43M     0 100% /snap/gtk-common-themes/701
/dev/loop4     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop5     squashfs   88M   88M     0 100% /snap/core/5662
/dev/loop6     squashfs   13M   13M     0 100% /snap/gnome-characters/124
/dev/loop0     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/nvme0n1p1 vfat       96M   55M   42M  58% /boot/efi
tmpfs          tmpfs     779M   72K  779M   1% /run/user/1000
/dev/loop7     squashfs   92M   92M     0 100% /snap/core/6531
/dev/loop8     squashfs   54M   54M     0 100% /snap/core18/782
/dev/loop9     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/70
/dev/loop10    squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/57
/dev/loop11    squashfs  4.2M  4.2M     0 100% /snap/gnome-calculator/352
/dev/loop12    squashfs   36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop13    squashfs   15M   15M     0 100% /snap/gnome-characters/206
/dev/loop14    squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/82
/dev/loop15    squashfs  144M  144M     0 100% /snap/gnome-3-28-1804/23
/dev/loop16    squashfs  185M  185M     0 100% /snap/tuxguitar-vs/9
/dev/sda1      fuseblk   468G  155M  467G   1% /media/jtrevorj/DATA
/dev/nvme0n1p3 fuseblk   119G   36G   83G  30% /media/jtrevorj/Acer

inxi -D
Drives:
  Local Storage: total: 1.03 TiB used: 88.33 GiB (8.4%) 
  ID-1: /dev/nvme0n1 vendor: Kingston model: RBUSNS8154P3128GJ1 
  size: 119.24 GiB 
  ID-2: /dev/sda vendor: Western Digital model: WD10EZEX-21WN4A0 
  size: 931.51 GiB

lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0 140.9M  1 loop /snap/gnome-3-26-1604/70
loop1         7:1    0   2.3M  1 loop /snap/gnome-calculator/238
loop2         7:2    0  42.1M  1 loop /snap/gtk-common-themes/701
loop3         7:3    0   3.7M  1 loop /snap/gnome-system-monitor/57
loop4         7:4    0  14.5M  1 loop /snap/gnome-logs/45
loop5         7:5    0  87.9M  1 loop /snap/core/5662
loop6         7:6    0    13M  1 loop /snap/gnome-characters/124
loop7         7:7    0  91.1M  1 loop /snap/core/6531
loop8         7:8    0  53.7M  1 loop /snap/core18/782
loop9         7:9    0   3.7M  1 loop /snap/gnome-system-monitor/70
loop10        7:10   0  1008K  1 loop /snap/gnome-logs/57
loop11        7:11   0     4M  1 loop /snap/gnome-calculator/352
loop12        7:12   0  35.3M  1 loop /snap/gtk-common-themes/1198
loop13        7:13   0  14.8M  1 loop /snap/gnome-characters/206
loop14        7:14   0 140.7M  1 loop /snap/gnome-3-26-1604/82
loop15        7:15   0 143.5M  1 loop /snap/gnome-3-28-1804/23
loop16        7:16   0 184.5M  1 loop /snap/tuxguitar-vs/9
sda           8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1        8:1    0   467G  0 part /media/jtrevorj/DATA
&#9500;&#9472;sda2        8:2    0   513M  0 part 
&#9492;&#9472;sda3        8:3    0   464G  0 part /
sr0          11:0    1  1024M  0 rom  
nvme0n1     259:0    0 119.2G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   100M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 118.1G  0 part /media/jtrevorj/Acer
&#9492;&#9472;nvme0n1p4 259:4    0     1G  0 part 

Just looking for help!

---

### Post by TheFu on 2019-03-24
Well, I can't be sure. Hard to read, but looks like you have 2 storage devices.  A 120G SSD and a 1TB regular HDD.  I don't know much about Windows, so I have to ignore that aspect.  I haven't dual-booted since around 2000. Generally, I use Windows when it runs inside a virtual machine.  Ok, enough of the things I can't help.

I would put these things on the SSD,, using encryption:
```
* / - 25G as ext4
* /boot - 1G as ext4
* /home - 5-15G as ext4
```
Because of the way that Ubuntu installs, using encryption wipes the entire installation storage, but any portable devices, like a laptop need to always be encrypted as much as possible. It also makes sending in SSDs and HDDs for warranty less concerning.  That is something you need to decide. In a dual boot setup, it won't be trivial to manually setup encryption.  In Ubuntu, using whole disk encryption also causes LVM to be used to simplify opening/decrypting 1 large partition when access to multiple logical volumes is needed.

If I'm hearing you correctly, encryption and using LVM probably aren't high on the list, especially with the new laws in AUS.

If your system is UEFI, you might need/have another partition that is FAT32 which has to be mounted to /boot/efi/.

I would limit /home data to things like config files and settings and any scripts you might create. I'd put those into ~/bin/, on the SSD. Then, like many ther people here, I'd use symbolic links from /home/trevor/Documents Photos, etc... and all those other directories that GUIs auto-create in HOME to a data partition (ext4) on the 1TB HDD. It needs to be ext4 (or some natively supported Linux file system) for a number of reasons. I'd setup the permissions so this was only available to my account.  

Media files that don't change - so videos and music would go into a different partition. If it needs to be shared with Windows, use NTFS.

Also, I didn't say anything about a swap partition. In general, that should be on slow storage and 4.1G in size. If you have more than 4G of RAM, then you cannot use hibernation if the swap is smaller than the RAM.  Standby does work fine.  The point of swap is 2 things - to expand the available memory beyond what is physically inside the system and to provide feedback by making the system feel slower to the end-user when swap is used, so the end-user can take appropriate actions - like closing down huge programs.  If swap is on an SSD, it might be too fast that we, end-users, won't notice.

I am not a fan of using any mount points under /media/  ... stuff there is seldom mounted in an efficient way and the OS will put other stuff under there like random USB storage.  This article explains what directories should be used for what: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)  All major Linux distros follow this.  You should too. Smart people came up with that standard and thought thru all sorts of things that you and I wouldn't consider.

Backups need to go to different physical storage. It is best if that is external, like USB3.  If it isn't clear why, ask.  In general, backups for each file system/partition/LV need to go onto a similar file system on the backup storage.  So, Linux file systems need to be backed up to a native Linux file system and NTFS storage can be backed up to NTFS storage.

So, there you have it - what I consider an "efficient setup" for the storage you have.  How to get there from what you have today depends on how easy it is to reconfigure Windows storage to make room and how solid your skills with grub and fstab modification is. None of it is hard, just lots of steps and lots of details that have to be handled perfectly.  
On Linux, as long as the storage and files are mounted where they are expected with a compatible file system, users, groups and other permissions, then the underlying storage doesn't really matter. And if mounting the storage to exactly the right location isn't possible, much of that can be fixed using either bind-mounts or hardlinking or symbolic linking.  These methods only work if the file system supports them, which all Linux file systems do. Windows support is, er, ... less.

As an example, here is my new laptop setup:```

$ df -Th
Filesystem                      Type      Size  Used Avail Use% Mounted on
/dev/sda2                       ext2      721M  142M  543M  21% /boot 
/dev/sda1                       vfat      511M  3.7M  508M   1% /boot/efi
/dev/mapper/ubuntu--vg-root     ext4       25G  7.3G   16G  32% /
/dev/mapper/ubuntu--vg-stuff    ext4       99G   95M   94G   1% /stuff
/dev/mapper/ubuntu--vg-home--lv ext4       74G   20G   51G  28% /home

$ sudo lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                         8:0    0 465.8G  0 disk
&#9500;&#9472;sda1                      8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                      8:2    0   732M  0 part  /boot
&#9500;&#9472;sda3                      8:3    0 464.6G  0 part
&#9474; &#9492;&#9472;sda3_crypt            253:0    0 464.6G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root     253:1    0    25G  0 lvm   /
&#9474;   &#9500;&#9472;ubuntu--vg-stuff    253:4    0   100G  0 lvm   /stuff
&#9474;   &#9500;&#9472;ubuntu--vg-swap_1   253:2    0   980M  0 lvm   [SWAP]
&#9474;   &#9492;&#9472;ubuntu--vg-home--lv 253:3    0    75G  0 lvm   /home

```
My disk is a 500G SSD, mostly empty, but also encrypted, as you can see. I use LVM, all logical volumes, volume-groups, and physical volumes are inside the encrypted partition (sda3), inside the LUKS container (sda3_crypt).   My backups are "pulled" by another system over the network.

Hopefully, someone with current Windows knowledge will respond on the things I cannot help about.  I would suspect that the core OS on the SSD and user directories + data on the HDD would be the recommendation, especially if Windows isn't used much.  Might be easiest to just move all of Windows off the SSD over to the HDD. I don't know. I haven't installed Windows since around 2010-ish and even then it was into a virtual machine.

---

### Post by Trevor Jones on 2019-03-25
Thanks TheFu. You have given this a lot of thought and consideration to answer my questions succinctly. I really appreciate your help

---

