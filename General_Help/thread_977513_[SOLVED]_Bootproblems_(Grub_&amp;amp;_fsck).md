---
title: "[SOLVED] Bootproblems (Grub &amp;amp; fsck)"
date: 2008-11-10
forum: General Help
---

### Post by tinmon on 2008-11-10
Hello,

I've run into two problems related to the boot process.

First I got a message that I should use fsck. I think I know why I need to do this: Either my root partition or one of the partitions on my external hd (or both) became too full. Wasn't paying attention when downloading and accepted the default value rather than the partion with 10GB free...

I have a dual boot and at this stage there was no problem booting Win XP.

Booted the LiveCD to backup the most important files and make some space on the two partitions. Switched between Win XP and LiveCD a couple of times.

Suddenly the boot to Win XP just gives me the grub prompt.

I can't really see what the problem is:

/boot/grub/menu.lst looks reasonably fine to me - here's what come's after the default options:

```

title		Ubuntu 7.10, kernel 2.6.22-15-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-386

title		Ubuntu 7.10, kernel 2.6.22-15-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro single
initrd		/boot/initrd.img-2.6.22-15-386

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.20-16-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.20-15-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu 7.10, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

/etc/fstab looks fine as well:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=d2191014-090b-4e93-9e98-49bb5f2f4a10 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=EA6C05646C052CBF /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=07b6240a-3768-4855-af08-591ccae43ac5 /media/hda4 ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=85162231-3927-46ed-855b-d394ca23830e none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Is there something causing both of these problems - something like one corrupted file - or are these two separate problems?

I'm in the process of upgrading from 7.10 but I thought it would be nice if I could fix this first and do an immediate fresh install only as a fallback plan.

---

### Post by caljohnsmith on 2008-11-10
So just to clarify, you can't boot into Ubuntu or Windows on your HDD right now? Do you have your Windows Install CD? I would begin by booting that, go to the "recovery console", and run:
```
fixboot
```
That will fix the boot code in the Windows boot sector in case that is the problem. Also I would do:
```
chkdsk /r
```
And run that as many times as it takes until it returns no errors. Also, how about posting:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
And lastly, I would recommend removing the "savedefault" and "makeactive" lines from your Windows entry:
```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1
```
Neither of those lines are necessary to boot Windows, and when you are having strange problems with Grub, it is best to remove anything extra to narrow down the range of possible problems.

---

### Post by tinmon on 2008-11-10
Here's the output from those commands:

**sudo fdisk -lu**

```
Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders, total 117304992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa1caa1ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    19535039     9767488+   7  HPFS/NTFS
/dev/sda2        19535040    66396644    23430802+  83  Linux
/dev/sda3       113258250   117290564     2016157+   5  Extended
/dev/sda4        66396645   113258249    23430802+  83  Linux
/dev/sda5       113258313   117290564     2016126   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   209712509   104856223+   c  W95 FAT32 (LBA)
/dev/sdb2       209712510   419425019   104856255   83  Linux
/dev/sdb3       767055555   976768064   104856255   83  Linux
```

[B]
sudo mount /dev/sda1 /mnt
ls -l /mnt
[/B]
```
total 1561063
-rwxrwxrwx 1 root root          0 2005-03-23 10:52 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        167 2005-03-23 11:40 AVM.log
-rwxrwxrwx 1 root root        167 2005-03-23 11:40 AVMP.log
-rwxrwxrwx 1 root root       4952 2004-08-04 12:00 Bootfont.bin
-rwxrwxrwx 1 root root        211 2005-04-02 10:00 boot.ini
drwxrwxrwx 1 root root       4096 2008-11-07 16:06 Config.Msi
-rwxrwxrwx 1 root root          0 2005-03-23 10:52 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-02-05 22:07 Documents and Settings
drwxrwxrwx 1 root root          0 2006-11-24 01:11 f515a47575ad3d3621eb99927467
-rwxrwxrwx 2 root root        856 2005-11-18 10:21 flashplayer.xpt
-rwxrwxrwx 1 root root          0 2005-03-23 10:52 IO.SYS
-rwxrwxrwx 1 root root          0 2005-03-23 10:52 MSDOS.SYS
-rwxrwxrwx 1 root root          0 2006-06-06 07:19 NeroTemp.nrg
-rwxrwxrwx 1 root root      47564 2004-08-04 12:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250560 2008-10-17 13:22 ntldr
-rwxrwxrwx 1 root root 1598029824 2008-11-07 08:42 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-11-07 16:05 Program
drwxrwxrwx 1 root root          0 2008-11-04 13:39 Program Files
drwxrwxrwx 1 root root          0 2005-04-27 18:38 RECYCLER
-rwxrwxrwx 1 root root         90 2005-03-23 11:18 setup.log
drwxrwxrwx 1 root root       4096 2005-04-02 10:00 System Volume Information
-rwxrwxrwx 1 root root        181 2005-03-23 11:20 TP.log
-rwxrwxrwx 2 root root        498 2008-11-07 16:06 updatedatfix.log
drwxrwxrwx 1 root root     155648 2008-11-07 08:45 WINDOWS

```

---

### Post by tinmon on 2008-11-10
> **caljohnsmith said:**
> So just to clarify, you can't boot into Ubuntu or Windows on your HDD right now? 

I suppose I could try to issue a Grub command at the CLI but no normal boot process last time I tried. Have deleted and moved some files since then so I will try to boot again to see if there still is a problem.


> Do you have your Windows Install CD?

Yes.
 
> And lastly, I would recommend removing the "savedefault" and "makeactive" lines from your Windows entry:
```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1
```
Neither of those lines are necessary to boot Windows, and when you are having strange problems with Grub, it is best to remove anything extra to narrow down the range of possible problems.

So XP isn't an unsupported operating system? I'll remove those lines then just in case they're causing this.

(Looking at the documentation for Grub I only see Win 95 given as an example of unsupported OS)
[http://orgs.man.ac.uk/documentation/grub/grub_4.html#SEC18]("http://orgs.man.ac.uk/documentation/grub/grub_4.html#SEC18")

BTW, the reason I gave lack of space on my internal and external HDD as the most probable cause is the error message I got.

Considering that my latest fresh install was Edgy (if I remember correctly) getting rid of old and dated things - like removing the "savedefault" and "makeactive" lines - might be even more important than making room on my hard drives.

There have been occassional hickups when booting but I can't give any specifics when that began or how often that occurs.

One example of the incidents is that X doesn't start but is ok after a reboot. In addition to that I can't boot any of the newer kernels I have installed. No problem with the even newer kernel on the LiveCd...

---

### Post by tinmon on 2008-11-11
Not sure if the glass is half empty or half full :confused: , but now I can at least boot into XP...  :)

:KS


[B]Q1: Does this mean that there's no longer any need to fix the boot sector?

[/B]When trying to boot Kubuntu the boot process began as normal but after a while it slowed down considerably. I didn't have the time to wait it out just then so I tried XP instead.

I'll continue to make some more room on my HDD.

**Q2: Would it be possible to run Aptitude on my HDD from the LiveCD** (via /media/...) or will it be confused and not find the packages to uninstall?

---

### Post by tinmon on 2008-11-12
OK, marking this thread as solved.

Managed to boot both XP and Kubuntu. Took a couple of rounds of fsck to do that and even then it felt a bit unstable. Froze up so I had to do the fsck loop a couple more times...

As I said, I will do a fresh install so if this is an annoying but temporary problem.

---

