---
title: "Windows 7 and grub"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by neerajvm on 2009-01-10
I've just loaded windows 7 beta on my pc containing Intrepid. Naturally, the install messed up grub. I reloaded grub. But somehow, windows 7 just does not load. Here's the extract from my menu.lst Any idea guys?


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7 beta
root		(hd0,0)
savedefault
makeactive
chainloader	+1


PS- I hope this is in the right section. Haven't used forums all that much before.

---

### Post by caljohnsmith on 2009-01-10
In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://internap.dl.sourceforge.net/sourceforge/bootinfoscript/boot_info_script.sh' && sudo bash boot_info_script.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by neerajvm on 2009-01-10
I'm guessing this is the relevant code. This is followed by menu.lst like I mentioned before.

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda8: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b0e2b0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sda2        39070080   156360644    58645282+   f  W95 Ext'd (LBA)
/dev/sda5        39070143    97675199    29302528+   7  HPFS/NTFS
/dev/sda6        97675263   135877769    19101253+   7  HPFS/NTFS
/dev/sda7       135877833   155862629     9992398+  83  Linux
/dev/sda8       155862693   156360644      248976   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AC1C70D01C7096D4" TYPE="ntfs" 
/dev/sda5: UUID="C814B7D414B7C42A" TYPE="ntfs" 
/dev/sda6: UUID="1EB04C08B04BE53D" TYPE="ntfs" 
/dev/sda7: UUID="50c78867-3147-441c-90a8-e307e797a518" TYPE="ext3" 
/dev/sda8: UUID="91d4bae7-86e9-4b04-9270-af746955fc8d" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/neerajvm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neerajvm)
/dev/sda5 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/disk-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================== sda1/Boot: ==================================

total 584
drwxrwxrwx 1 root root   4096 2009-01-10 07:52 .
drwxrwxrwx 1 root root   4096 2009-01-10 18:44 ..
-rwxrwxrwx 1 root root  24576 2009-01-09 18:52 BCD
-rwxrwxrwx 1 root root  21504 2009-01-09 18:41 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-10 07:52 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-10 07:52 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-10 07:52 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-10 07:52 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-10 07:52 da-DK
drwxrwxrwx 1 root root      0 2009-01-10 07:52 de-DE
drwxrwxrwx 1 root root      0 2009-01-10 07:52 el-GR
drwxrwxrwx 1 root root      0 2009-01-10 07:52 en-US
drwxrwxrwx 1 root root      0 2009-01-10 07:52 es-ES
drwxrwxrwx 1 root root      0 2009-01-10 07:52 fi-FI
drwxrwxrwx 1 root root      0 2009-01-10 07:52 Fonts
drwxrwxrwx 1 root root      0 2009-01-10 07:52 fr-FR
drwxrwxrwx 1 root root      0 2009-01-10 07:52 hu-HU
drwxrwxrwx 1 root root      0 2009-01-10 07:52 it-IT
drwxrwxrwx 1 root root      0 2009-01-10 07:52 ja-JP
drwxrwxrwx 1 root root      0 2009-01-10 07:52 ko-KR
-rwxrwxrwx 1 root root 473864 2008-12-13 12:31 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-10 07:52 nb-NO
drwxrwxrwx 1 root root      0 2009-01-10 07:52 nl-NL
drwxrwxrwx 1 root root      0 2009-01-10 07:52 pl-PL
drwxrwxrwx 1 root root      0 2009-01-10 07:52 pt-BR
drwxrwxrwx 1 root root      0 2009-01-10 07:52 pt-PT
drwxrwxrwx 1 root root      0 2009-01-10 07:52 ru-RU
drwxrwxrwx 1 root root      0 2009-01-10 07:52 sv-SE
drwxrwxrwx 1 root root      0 2009-01-10 07:52 tr-TR
drwxrwxrwx 1 root root      0 2009-01-10 07:52 zh-CN
drwxrwxrwx 1 root root      0 2009-01-10 07:52 zh-HK
drwxrwxrwx 1 root root      0 2009-01-10 07:52 zh-TW

```

---

### Post by caljohnsmith on 2009-01-10
It looks like Vista is on sda1, but you have two other NTFS partitions, sda5 and sda6, so did you install Windows 7 to one of those partitions? In order to see where Windows 7 is, and also where it's boot files might be, how about posting:
```
sudo mkdir /mnt/sda1 /mnt/sda5 /mnt/sda6
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
sudo mount /dev/sda6 /mnt/sda6
ls -l /mnt/sda1 /mnt/sda5 /mnt/sda6
```

---

### Post by neerajvm on 2009-01-10
Nope. It's Windows 7 on sda1. I haven't installed Vista and yes I do have 2 other NTFS partitions, but sda1 is the primary/boot partition. sda1 used to contain XP, which I trashed(formatted) for win 7. And I know, it's a beta. Just wanted to try it out.

---

