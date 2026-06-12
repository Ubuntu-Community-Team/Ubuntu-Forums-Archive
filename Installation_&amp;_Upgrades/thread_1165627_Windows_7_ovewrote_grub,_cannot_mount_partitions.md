---
title: "Windows 7 ovewrote grub, cannot mount partitions"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by NevNiv on 2009-05-20
Hello, I apologize in advance if this belonged in General Help.  I wasn't sure.
[B]
I recently installed Windows 7, and I forgot that it would screw up my bootloader.  I use grub with mostly default settings.  I want to get grub back in action so I can access my Ubuntu installation again.[/B]

I pulled up a few guides (here's one [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ) that said to boot to the LiveCD (which I'm currently on), and to type the following

[I]find /boot/grub/stage1

I get in response "Error 15: File not found."[/I]

From what I understand, this was to find my Linux partition.  So I tried an alternative I also found online:
[I]
root@ubuntu:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaff3aff3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       12748    71682030    7  HPFS/NTFS
/dev/sda3           12749       20398    61440000    7  HPFS/NTFS
/dev/sda4           35993       38913    23462932+   5  Extended
/dev/sda5           38671       38913     1951897+  82  Linux swap / Solaris[/I]

So, /dev/sda4 is my linux partition, right?  Next I tried this

[I]grub> root (hd0,3)

grub> setup (hd0)

Error 17: Cannot mount selected partition[/I]

](*,)

I also tried a million other combinations of the two above commands, I seem to always get the cannot mount error.

I also tried the mount -t method and ended up getting "already mounted or busy" on some partitions, and in sda4 in particular, I got

[I]mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]


I am running 8.10 Intrepid Ibex.

Thank you for your time.

---

### Post by utnubuuser on 2009-05-20
When you tried the > find /boot/grub/stage1
with no success, did you try the alternative> find grub/stage1

I had a similar experience at one time,  though I cannot remember if I finally succeeded or ended up re-installing Ubuntu.  

Do you have a seperate /home partition so you can re-install the OS and retain your settings etc?

---

### Post by Ceiber Boy on 2009-05-20
If you don't have any valuable data on your linux partition, just format the partition and reinstall linux

or

use your live cd to copy your data from your linux partition to your windows partition and onceagain reinstall!

i know that this dose not directly answer you question but i hope it helps

---

### Post by presence1960 on 2009-05-20
to get a better look at your present setup boot from the Live CD and download to your Desktop the Boot Info Script from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and run this command > sudo bash ~/Desktop/boot_info_script*.sh

This will produce a RESULTS.txt file on your desktop. Paste the contents of that file here. highlight all text and click # on the toolbar.

---

### Post by dipaish on 2009-05-20
Nothing to worry dude. Boot in your windows. Download application named easy bcd (search it in google). I am sure i dont have to explan more how to use that application because once you run it you know what to do. Best of luck. If you are still unable to manage it write me . I will explain in detail

---

### Post by Gadgetech on 2009-05-20
Did you make sure to sudo to root first?
```
sudo su
grub
grub> root (hd0,3)
grub> setup (hd0)
```

[URL="http://tuxtweaks.com/2009/01/windows-7-hosed-my-boot-record/"]
Windows 7 overwrote my boot sector[/URL] too.

If it still doesn't work, you may need to repair the file system with e2fsck. Assuming you're still root...
```
umount /dev/sda4
e2fsck -p /dev/sda4
```

Then try the grub commands again.

---

### Post by NevNiv on 2009-05-21
Crap! I'm editing my post because I just realized something horrible.  My linux partition is GONE!

In fdisk, sda4 is only one block, and it seems to be the free space in between the Windows 7 installation and the swap partition.  I did not know that free space could be assigned a name (sda4).

Somehow my linux partition disappeared when I installed Windows 7.  I am sure I didn't delete it when I created the Windows 7 partition.  I picked the manual option and created a 60gb partition on my own.

I'm going to try to restore the partition with Partition Table Doctor, as nothing should have been written to the space it was in.

**Below is what I had originally written in this post.  It no longer pertains to my issue**
> **utnubuuser said:**
> When you tried the 
with no success, did you try the alternative

I had a similar experience at one time,  though I cannot remember if I finally succeeded or ended up re-installing Ubuntu.  

Do you have a seperate /home partition so you can re-install the OS and retain your settings etc?

Yes, the alternative didn't work either.

I do not remember if I have a separate /home.  I do not think this PC does.  I think if I did, it would be another partition in the list I got from my fdisk. :(

> **Gadgetech said:**
> Did you make sure to sudo to root first?
```
sudo su
grub
grub> root (hd0,3)
grub> setup (hd0)
```

[URL="http://tuxtweaks.com/2009/01/windows-7-hosed-my-boot-record/"]
Windows 7 overwrote my boot sector[/URL] too.

If it still doesn't work, you may need to repair the file system with e2fsck. Assuming you're still root...
```
umount /dev/sda4
e2fsck -p /dev/sda4
```

Then try the grub commands again.
Output:
[I]root@ubuntu:~# e2fsck -p /dev/sda4
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?[/I]

Scary-sounding error. :confused:

> **presence1960 said:**
> to get a better look at your present setup boot from the Live CD and download to your Desktop the Boot Info Script from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and run this command 

This will produce a RESULTS.txt file on your desktop. Paste the contents of that file here. highlight all text and click # on the toolbar.

Ah, very neat!

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaff3aff3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   204,796,619   143,364,060   7 HPFS/NTFS
/dev/sda3         204,797,952   327,677,951   122,880,000   7 HPFS/NTFS
/dev/sda4         578,211,480   625,137,344    46,925,865   5 Extended
/dev/sda5         621,233,550   625,137,344     3,903,795  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D08C3B418C3B2200" TYPE="ntfs" 
/dev/sda2: UUID="FA580E90580E4BB7" LABEL="Data" TYPE="ntfs" 
/dev/sda3: UUID="5808E9FD08E9DA50" TYPE="ntfs" 
/dev/sda5: UUID="df856b6c-6967-4d68-b33e-c59ebae535c0" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN

=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda2: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

I am a little confused by the results.  I think it misinterpreted one of my NTFS partitions to be Vista.  I should have an XP install, a Windows 7 install, and an NTFS drive I created from XP to stick My Documents in.

@dipaish - LOL, just tried that BCD thing.  I told it to put grub on BOOT, I believe.  Now my PC just boots to a grub> prompt, hahahahaha.

I think it's strange that I can't seem to see the files on my linux partition.  From the liveCD, shouldn't I see my linux partition?  If I could just get to the files I would just take them off and reformat.  I wanted to fix this without doing that, but it seems tough.  I'm wondering if Windows 7 decided to partially axe my Linux partition.

P.S. Thank you to everyone for the help!

---

