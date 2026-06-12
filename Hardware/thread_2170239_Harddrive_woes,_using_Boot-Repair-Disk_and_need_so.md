---
title: "Harddrive woes, using Boot-Repair-Disk and need some assistance"
date: 2013-08-25
forum: Hardware
---

### Post by AbsoluteZ3r0 on 2013-08-25
Hello all,

I tried installing Windoz 7 on one of my harddrives awhile back. It ended up not working correctly, so I deleted it. At this same time I had another harddrive running gnu/linux. 
When I first tried to boot my linux drive back up I received a "Grub boot error".
I searched for a long while and finally found 'Boot-Repair-Disk'. I downloaded it, burned it and booted into it just a few moments ago.

The issue I am having is that the program gave me a text file giving a readout on my disk that has the boot problem, but the program would not fix it.
So that is why I am here. To ask if any of you could please give me guidance on what I should try next. I would really like to get this drive back up and running. It has a lot of files I need on it.

 

 Here is the contents of the text file:
```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       976,596       976,563 BIOS Boot partition

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/7508/mounts) leaked on lvscan invocation. Parent PID 11740: bash
File descriptor 12 (/usr/share/icons/lubuntu/places/16/folder.svg) leaked on lvscan invocation. Parent PID 11740: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-08-25__15h58 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
File descriptor 8 (/proc/7508/mounts) leaked on lvs invocation. Parent PID 8874: /bin/sh
File descriptor 12 (/usr/share/icons/lubuntu/places/16/folder.svg) leaked on lvs invocation. Parent PID 8874: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 24avr2013, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: ATA Hitachi HDS5C302 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
1      17.4kB  500MB  500MB                     bios_grub


                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: /dev/sr0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:2000GB:scsi:512:512:gpt:ATA Hitachi HDS5C302;
1:17.4kB:500MB:500MB:::bios_grub;

                                                                            Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: /dev/sr0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)


=================== ls:
/sys/block/sda  (filtered):  alignment_offset bdi capability dev device  discard_alignment events events_async events_poll_msecs ext_range  holders inflight power queue range removable ro sda1 size slaves stat  subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset  bdi capability dev device discard_alignment events events_async  events_poll_msecs ext_range holders inflight power queue range removable  ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm  ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console  core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse  hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet input kmsg kvm log mapper  mcelog mem net network_latency network_throughput null oldmem port ppp  psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 sg1 shm snapshot snd  sr0 stderr stdin stdout uinput urandom usb vga_arbiter vhost-net  watchdog zero
ls /dev/mapper:  control

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G   19M  3.9G   1% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      794M  848K  793M   1% /run
/dev/sr0       iso9660    508M  508M     0 100% /cdrom
/dev/loop0     squashfs   435M  435M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  584K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G     0  3.9G   0% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69caad17

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT


Error: no partitions

=================== Default settings
Recommended-Repair
This setting would reinstall the  of .
Additional repair would be performed:  repair-filesystems

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
```


Thank you all in advance!

---

### Post by oldfred on 2013-08-25
You really only have grub on sda, your 2TB drive. Did you have an install on it? If so it is missing.

You do have a gpt partitioned drive, not MBR(msdos). Your bios-grub is large as it only needs to be 1 or at most 2MB unformatted with the bios_grub flag. Yours is 500MB. 

Windows only boots from gpt partitioned drives with UEFI. Ubuntu can boot in UEFI or BIOS mode from gpt drives. But with BIOS you have the bios_grub for grub2 to install its boot loader into the MBR correctly or you have an efi partition at the beginning of the drive if booting in UEFI mode. On new drives I suggest both or space for both,  in case later you want to change boot modes. Adding an efi partition at start of drive, after you have half filled a 2TB  drive can be difficult.

If install was on other drive then maybe you were not using this drive?

 Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)


 repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by AbsoluteZ3r0 on 2013-08-27
Yes, I did have an install on the 2TB drive. 
What happened was that I had the 2TB drive plugged in with a 500GB drive. The 500GB drive was installing Windoz 7. At the time I had unplugged the 2TB.
I tried to boot into Windoz 7 and started to have problems so I backed off and was just going to reformat it and use it for extra space.
When I plugged the 2TB with ubuntu on it back in, that is where the problems started.
I was unable to boot the drive at all.
I had a small 128GB drive around so I put Mint on it to see if I could just grab my files off of the 2TB and then just reformat it and put Ubuntu back on it.
When I tried this the 2TB didn't even show up. I tried to mount but it wouldn't appear. So I got worried and tried the boot-repair and then came here.
I will try the above.
I will have the Mint harddrive try to repair the 2TB Ubuntu one and report back.
Thanks you!

---

### Post by oldfred on 2013-08-27
You might want to plug all the drives in and just run the BootInfo report to see what is where and document that.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by AbsoluteZ3r0 on 2013-08-27
Alright, thank you!
I was doing some more research and downloaded a gparted-live disk and put it in.
When I load it up I see the boot partition but then the rest is all 'unallocated'.
So I am wondering if this is a deeper issue...
Do you know, is this corrupted?
If so can I run a program to create an image of the files or even extract files from it?
Thank you again for all of your help so far!

---

### Post by AbsoluteZ3r0 on 2013-08-27
Here is the link to the Bootinfo report:

[http://paste.ubuntu.com/6034558/](http://paste.ubuntu.com/6034558/)

---

### Post by oldfred on 2013-08-27
You can use testdisk to see if it can find missing partitions as posted in #2. And sometimes with deeper search it will find files.

---

