---
title: "ubuntu install - now all xp files missing"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by cooperle on 2009-05-25
I lost quite a few files I need to complete my PhD (in three months) so I could really use some help here.

Installed Ubuntu 9.04 from CD yesterday, chose option to install "side by side" for dual boot on C:.  I get an error at the end of the install claiming the install disk was corrupt, but Ubuntu boots right up after the install and everything seems cool.

I restart the computer and it goes to reboot to windows XP automatically.  After the progress bar screen I get the blue screen of death, computer restarts too fast for me to read the message (probably a bad sign lol). I try to run recovery from the XP CD and it craps out.

I have a blank unused disk laying here so install XP on it figuring I can just read & copy my old files off C: - no such luck.  The disk C: looks blank from the new XP install.  Using testdisk_win I can see an NTFS partition and the Linux partition but still can't find my files.

---

### Post by vpnm_87 on 2009-05-25
thought of sharing some ideas since am also a newbie:-)
did u manage to work in installed ubuntu atleast once or u havent even logged into ubuntu after installation...

try pressing F8 continuously after ur POST screen..
if u see both XP and Ubuntu option in OS choices menu it ll help u i think
if u see only XP then u got to do some extra hard work:-)

---

### Post by Sef on 2009-05-25
1) Don't use that hard drive or you could end up overwriting the files, if they still exist.

2) Use the Live CD:  Applications > Accessories > Terminal

the copy and paste this command:

```
sudo fdisk -l
```  That will show you the partitions on your hard drive.  Copy and paste the results here.

---

### Post by cooperle on 2009-05-25
Thank you Sef.  Here is the output.  There is still an NTFS partition there but I can't seem to locate any files on it besides autoexec.bat and some other small things.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90d090d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60475   485765406    7  HPFS/NTFS
/dev/sda2           60476       60801     2618595    5  Extended
/dev/sda5           60476       60779     2441848+  83  Linux
/dev/sda6           60780       60801      176683+  82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcd135c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182400  1465127968+   7  HPFS/NTFS

Disk /dev/sdc: 521 MB, 521928192 bytes
129 heads, 11 sectors/track, 718 cylinders
Units = cylinders of 1419 * 512 = 726528 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         719      509690    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(722, 128, 11) logical=(718, 49, 10)
ubuntu@ubuntu:~$

---

### Post by cooperle on 2009-05-25
I mounted /dev/sda1 to look for files and all I found were some small random windows crap like autoexec.bat and config.sys.
 
Cany anyone give me some guidance about how to proceed?

---

### Post by ronparent on 2009-05-25
Your fdisk output looks suspiciouly like you may have inadvertently installed on the first drive of a raid0 set. That is not a foregone conclusion but a strong possibility. 

If it was a raid set then you may have pretty much lost everything that was on at least the former extended partition. If you must absolutely know bad news for sure then you could install and run dmraid from a live cd to discover the metadata that would still be on the disk. There is only a remote posibily that anything is recoverable. If dmraid could assemble some of what remains, you might be able transfer anything that was worth recovering from a more or less intact partition to a safer place. Everything would have to be done from a ubuntu live cd since the installed ubuntu would be unavailable while the drive is accessed as a raid. I don't hold out much hope, however, since It is a wild scheme I've just now conjectored and I have no knowledge its ever succeeded. If you have any interest I can give you specific instructions.

---

