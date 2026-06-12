---
title: "Read-Only Drive"
date: 2021-05-12
forum: Hardware
---

### Post by devdlp on 2021-05-12
i just formatted my second hdd to /stuff and got it to auto mount but it shows read-only when i try to install a steam game to it how do
 i fix this please? Ive tried a couple things fstab rw, remount etc.. but not fixed could i have some support with this please?

---

### Post by ajgreeny on 2021-05-12
What filesystem?

If you formatted to ext4 or another Linux filesystem it will be owned by root unless you change ownership of the mountpoint to yourself as user with ```
sudo chown -R $USER:USER /mountpoint/pathway
``` Use the full pathway of the mountpoint, eg, /mnt/stuff but create that mountpoint first if it does not already exist with ```
sudo mkdir /mnt/stuff
```
Show us the content of your /etc/fstab file with ```
cat /etc/fstab
```

---

### Post by TheFu on 2021-05-12
Which file system?
Which userid is the owner for the mount point (after mounting) and for all directories and files below it?
Sounds like a normal Unix permissions issue.

[LIST=1]
[*]Mount the storage
[*]Run **df -Th** to see which file system it has and that it is actually mounted where you think.
[*]Run **ls -al /on/the/directory/where/it/is/mounted**
[/LIST]


Post those outputs here, wrapped in code tags, if you need more help.
Code Tags how-to: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by devdlp on 2021-05-12
> **ajgreeny said:**
> What filesystem?

If you formatted to ext4 or another Linux filesystem it will be owned by root unless you change ownership of the mountpoint to yourself as user with ```
sudo chown -R $USER:USER /mountpoint/pathway
``` Use the full pathway of the mountpoint, eg, /mnt/stuff but create that mountpoint first if it does not already exist with ```
sudo mkdir /mnt/stuff
```
Show us the content of your /etc/fstab file with ```
cat /etc/fstab
```

deven@TahmOpal:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=1b287776-177f-4665-b9e8-8ed03a5df87b /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=7E2F-24D4  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

UUID=e9e93910-61e5-4b1c-8244-b4a394fe1ac7 /stuff ext4  nofail,noatime,errors=remount-ro  0  1
deven@TahmOpal:~$

---

### Post by devdlp on 2021-05-12
i changed ext4 to ext3 becuase thats thye format its in

---

### Post by devdlp on 2021-05-12
deven@TahmOpal:~$ sudo chown -R $USER:deven /dev/sdb1
[sudo] password for deven:

---

### Post by devdlp on 2021-05-12
im not understanding this at all

---

### Post by TheFu on 2021-05-12
sudo chown -R $USER:deven /dev/sdb1
is wrong.
Use: 
```
sudo chown -R $USER:deven /stuff
```
Actually, 
```
sudo chown -R $USER:$USER /stuff
```
is probably better for 99% of people viewing here.

**chown** only works when native Linux file systems are used.
chown does not work for NTFS, FAT32, vfat, exfat file systems. That's for people lurking later.

ext4 is probably the best choice as a file system on Linux today, lacking any other specific need with either spinning disk or SSD is involved.  For SDHC or USB-flash storage, there are better choices which are kinder towards the life-span of the storage.

---

### Post by devdlp on 2021-05-13
> **TheFu said:**
> sudo chown -R $USER:deven /dev/sdb1
is wrong.
Use: 
```
sudo chown -R $USER:deven /stuff
```
Actually, 
```
sudo chown -R $USER:$USER /stuff
```
is probably better for 99% of people viewing here.

**chown** only works when native Linux file systems are used.
chown does not work for NTFS, FAT32, vfat, exfat file systems. That's for people lurking later.

ext4 is probably the best choice as a file system on Linux today, lacking any other specific need with either spinning disk or SSD is involved.  For SDHC or USB-flash storage, there are better choices which are kinder towards the life-span of the storage.

wow that worked!!! your awesome man!! Thanks alot

---

### Post by TheFu on 2021-05-13
ajgreeny provided the command. It just wasn't understood, I suppose.  We all have blinders, sometimes.

Anyway, if this is solved, help out the community and use the "Thread Tools" button near the top to mark it SOLVED, so people find it or don't try to help now that it is done. Save everyone some time. Please.

---

