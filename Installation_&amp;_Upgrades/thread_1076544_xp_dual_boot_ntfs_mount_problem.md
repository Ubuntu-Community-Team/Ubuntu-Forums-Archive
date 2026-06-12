---
title: "xp dual boot ntfs mount problem"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by michael.j.jacobsen on 2009-02-21
I am running a dual boot Ubuntu 8.10 / XP on my laptop and since updating from 8.04 I suddenly cant mount any ntfs partitions with my files on it or ntfs usb hard drives. I have read other posts but cant get anywhere.
Initially whenever i tried to mount any ntfs drive I got an error message telling me to go back into windows and safely remove the drive or force mount it. Now after some fidling with NTFS configuration tool and trying terminal commands I am told I cant access the partition with my files on it because I am not privilidged to mount it. I still get the force mount error on my usb hard drive.

the fdisk output is

 Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26d126d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3919    31479336    7  HPFS/NTFS
/dev/sda2            3920       30401   212716665    5  Extended
/dev/sda5            3920        4860     7558551   bc  Unknown
/dev/sda6            4861       28346   188651261+   7  HPFS/NTFS
/dev/sda7           28347       30309    15767766   83  Linux
/dev/sda8           30310       30401      738958+  82  Linux swap / Solaris
michael@michael-laptop:~$ 

sda1 seems to be my c: drive with windows and program files on it.
sda6 is the partition I need to mount with my personal files on it, no programs.
sda5 is I think my accronis secure zone with backups on it but i'm not sure.

I'm a little new to terminals and stuff.

---

### Post by dstew on 2009-02-21
Have you tried to mount the partition using the command line? If not, open a terminal window (I am not sure about 8.10, but in 8.04 it is in Applications --> Accessories --> Terminal). You need to first create a mount point for the partition, which is just a directory:```
sudo mkdir /mnt/storage
```Of course you can give it a name other than "storage" if you want. Then, try to mount the partition to the mount point:```
sudo mount -t ntfs /dev/sda6 /mnt/storage
```Post to the forum any error messages you get. If you are successful, you should be able to see the directory of the storage partition:```
ls -l /mnt/storage
```

---

### Post by michael.j.jacobsen on 2009-02-21
Tried to mount from terminal but no joy again

michael@michael-laptop:~$ sudo mkdir /mnt/files
[sudo] password for michael: 
michael@michael-laptop:~$ sudo mount -t ntfs /dev/sda6 /mnt/files
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 /mnt/files -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 /mnt/files ntfs-3g force 0 0
michael@michael-laptop:~$

---

### Post by michael.j.jacobsen on 2009-02-21
Ahhhhh Success. with my partition at least. had to reforce the mount and restart. will keep fidling with usb drive. thanks for help

---

### Post by dstew on 2009-02-21
It could be there is something wrong with the file system on that partition. You should go into Windows and run a file system check on it. The Windows XP command is **[chkdsk]("http://www.updatexp.com/windows-xp-chkdsk.html")**. If the partition in question is d:, the command would be```
chkdsk d:
```

---

