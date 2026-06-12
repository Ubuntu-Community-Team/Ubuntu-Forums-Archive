---
title: "Mass USB Storage Problem"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by michaeljb2005 on 2006-06-26
I'm trying to mount a usb drive as /media/storage at bootup but the drive is not being mounted at startup.  I don't have it doing passes on the drive because everytime at startup it stops at a terminal in some sort of mid sentence.  If I do ctrl-D it boots and it will mount the drive on bootup.  But I don't want it starting up with a terminal.  I want it to boot straight in.  But like I said before.  When it boots straight in it doesn't mount the drive at the specified mount point in fstab.  It mounts it at some sort of tmp location.  I have to disable and then reenable at the correct mount point to get it to mount correctly.  I want to have my cake and eat it too, but for some reason it's not mounting correctly.  Any thoughts?

---

### Post by tonyr on 2006-06-26
USB devices are notoriously slow when it comes to recognition/mounting.  I don't 
remember exactly all of the magic, but you need to delay the boot sequence somehow
to let the hardware recognize the USB device before **mount** tries to do
anything with it.  Look for the keyword **delay** in relation to GRUB and
the **kernel** line options.  You can search in these forums for similar
USB boot/mount experiences.

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]USB devices are notoriously slow when it comes to recognition/mounting.  I don't 
remember exactly all of the magic, but you need to delay the boot sequence somehow
to let the hardware recognize the USB device before **mount** tries to do
anything with it.  Look for the keyword **delay** in relation to GRUB and
the **kernel** line options.  You can search in these forums for similar
USB boot/mount experiences.[/QUOTE]

I tried the boot delay with no success.

---

### Post by tonyr on 2006-06-26
Did you use a value of 10seconds or 15seconds (as I recall, the value is in tenths
of a second, so 10s->100, 15s->150).  This is about as far as my knowlege on
this issue goes.

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]Did you use a value of 10seconds or 15seconds (as I recall, the value is in tenths
of a second, so 10s->100, 15s->150).  This is about as far as my knowlege on
this issue goes.[/QUOTE]

I just put rootdelay=10. Is that correct?

---

### Post by tonyr on 2006-06-26
Yes, that's it as far as I know.

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]Yes, that's it as far as I know.[/QUOTE]

Well that did not seem to fix the problem.  Thank you for the suggestion though.

---

### Post by tonyr on 2006-06-26
I tried to replicate the problem.  I have Ubuntu 6.0.6 LTS updated a couple of days
ago.  I have a 6GB drive in an external USB case.  The drive has
three partitions:
```

Disk /dev/sda: 6007 MB, 6007357440 bytes
240 heads, 63 sectors/track, 776 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         700     5291968+  83  Linux
/dev/sda2             701         768      514080   82  Linux swap / Solaris
/dev/sda3             769         776       60480   83  Linux

```

With one external usb drive, the system should assign it as **sda**.  I 
created a directory **/media/storage**, and added this line to my **/etc/fstab**:
```

/dev/sda1       /media/storage  ext3    rw,nosuid,nodev 0       0

```

Then rebooted with no problem.  When I did **mount** in a terminal, it showed
```

:~> mount
/dev/hda7 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw)
/dev/hda2 on /media/hda2 type ntfs (rw)
/dev/hda3 on /media/hda3 type ext2 (rw)
/dev/hda5 on /media/hda5 type ext2 (rw)
/dev/hda8 on /media/hda8 type vfat (rw,umask=0)
/dev/hda9 on /media/hda9 type ext2 (rw)
/dev/sda1 on /media/storage type ext3 (rw,nosuid,nodev)
/dev/sda3 on /media/usbdisk type ext3 (rw,nosuid,nodev)

```

It recognized my specific **mount** entry in fstab, and 'did the right thing'
for the other partition, creating a mount point as necessary.

What's different about your setup?

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]I tried to replicate the problem.  I have Ubuntu 6.0.6 LTS updated a couple of days
ago.  I have a 6GB drive in an external USB case.  The drive has
three partitions:
```

Disk /dev/sda: 6007 MB, 6007357440 bytes
240 heads, 63 sectors/track, 776 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         700     5291968+  83  Linux
/dev/sda2             701         768      514080   82  Linux swap / Solaris
/dev/sda3             769         776       60480   83  Linux

```

With one external usb drive, the system should assign it as **sda**.  I 
created a directory **/media/storage**, and added this line to my **/etc/fstab**:
```

/dev/sda1       /media/storage  ext3    rw,nosuid,nodev 0       0

```

Then rebooted with no problem.  When I did **mount** in a terminal, it showed
```

:~> mount
/dev/hda7 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw)
/dev/hda2 on /media/hda2 type ntfs (rw)
/dev/hda3 on /media/hda3 type ext2 (rw)
/dev/hda5 on /media/hda5 type ext2 (rw)
/dev/hda8 on /media/hda8 type vfat (rw,umask=0)
/dev/hda9 on /media/hda9 type ext2 (rw)
/dev/sda1 on /media/storage type ext3 (rw,nosuid,nodev)
/dev/sda3 on /media/usbdisk type ext3 (rw,nosuid,nodev)

```

It recognized my specific **mount** entry in fstab, and 'did the right thing'
for the other partition, creating a mount point as necessary.

What's different about your setup?[/QUOTE]

/dev/sda1       /media/storage  ext3    rw,nosuid,nodev 0       0 is different I don't have rw,nosuid,nodev on there.  Am I supposed to?

---

### Post by tonyr on 2006-06-26
[QUOTE=michaeljb2005]/dev/sda1       /media/storage  ext3    rw,nosuid,nodev 0       0 is different I don't have rw,nosuid,nodev on there.  Am I supposed to?[/QUOTE]

I don't really know.  When I started,  I didn't use any **fstab** entry, and both partitions
showed up mounted anyway.  Those were the options that were reported, the 
**defaults**, maybe.  I just copied those.  See **man mount** and **man fstab**
for more info about what, exactly, they mean.

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]I don't really know.  When I started,  I didn't use any **fstab** entry, and both partitions
showed up mounted anyway.  Those were the options that were reported, the 
**defaults**, maybe.  I just copied those.  See **man mount** and **man fstab**
for more info about what, exactly, they mean.[/QUOTE]

I'm at work right now.  But let me get home and do the things you did, show you my partition layout and then you can let me know what you think?

---

### Post by tonyr on 2006-06-26
Okee Dokee.

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]Okee Dokee.[/QUOTE]

What are the commands you used to get the start and end block information?

---

### Post by tonyr on 2006-06-26
```

sudo fdisk -l

```

should show you all partition definitions for all hard drives.

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]```

sudo fdisk -l

```

should show you all partition definitions for all hard drives.[/QUOTE]

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        7296    43246980    f  W95 Ext'd (LBA)
/dev/sda5            1913        1978      530113+  82  Linux swap / Solaris
/dev/sda6            1979        3890    15358108+  83  Linux
/dev/sda7            3891        7296    27358663+  83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10581    84991851    7  HPFS/NTFS
/dev/sdb2           10582       30515   160119855    5  Extended
/dev/sdb5           10582       29368   150906546   83  Linux
/dev/sdb6           29369       30515     9213246    b  W95 FAT32

"/dev/sdb5           10582       29368   150906546   83  Linux" is the one that is giving me trouble.

fstab shows

/dev/sdb5	/media/storage	ext3	defaults	0	0

for this drive.

---

### Post by tonyr on 2006-06-26
I'm running out of ideas.  The fact that you have an **sda** device (internal?) 
makes this a situation I am not  familiar with.  Is your internal drive SCSI,
or is it SATA, or something else?

Are the other **sdb** partitions being mounted at all? via fstab?
 Can you post the fstan file here?

---

### Post by michaeljb2005 on 2006-06-26
[QUOTE=tonyr]I'm running out of ideas.  The fact that you have an **sda** device (internal?) 
makes this a situation I am not  familiar with.  Is your internal drive SCSI,
or is it SATA, or something else?

Are the other **sdb** partitions being mounted at all? via fstab?
 Can you post the fstan file here?[/QUOTE]

This is a notebook inspiron 9300.

Here's the fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb5	/media/storage	ext3	defaults	0	0

sda is an internal drive.
sdb is the external usb drive.
The only partition of the external usb drive i'm having trouble with is the /dev/sdb5.

I use the external drive for backup and mass storage.

---

### Post by tonyr on 2006-06-27
These are some specs I found for an Inspiron 9300:
> 
17" Widescreen WUXGA+ 1920x1200 with XBrite display
1.66ghz Pentium-M 667mhz FSB 2MB L2 Cache CPU
GeForce 6800 Ultra 256MB Dedicated GDDR3 PCIe graphics card
1GB of DDR2 PC4300 Dual-Channel RAM
80GB SATA Hard Drive
54G b/g wireless
Bluetooth 3mbps (BluCore 4) integrated
DVD/CD-RW
USB 2.0 ports out the *******
DVI out, dual monitor support
TV out
6 cell battery

Does that look about right?  The internal drive size  and memory may not be exactly the
same.  I think SATA drives go through as SCSI emulation, so they show up as
**/dev/sdx**.  It may be that USB drives and **ntfs** partitions don't behave very
well together.  The only thing I can suggest at this point is to change the **0 1**
at the end of the sdb1 line to **0 0**, bypassing the integrity check. If that works,
you could also try **0 2**.  **man fstab** says that only the **root** partition
should have a **passno** of 1, and all other partitions to be checked have a
**passno** of 2.

In your first post you said you weren't doing any check passes on the **sdb** devices,
but the **fstab** entry for **/dev/sdb1** indicates that a check pass is being
done,

---

### Post by michaeljb2005 on 2006-06-27
[QUOTE=tonyr]These are some specs I found for an Inspiron 9300:

Does that look about right?  The internal drive size  and memory may not be exactly the
same.  I think SATA drives go through as SCSI emulation, so they show up as
**/dev/sdx**.  It may be that USB drives and **ntfs** partitions don't behave very
well together.  The only thing I can suggest at this point is to change the **0 1**
at the end of the sdb1 line to **0 0**, bypassing the integrity check. If that works,
you could also try **0 2**.  **man fstab** says that only the **root** partition
should have a **passno** of 1, and all other partitions to be checked have a
**passno** of 2.

In your first post you said you weren't doing any check passes on the **sdb** devices,
but the **fstab** entry for **/dev/sdb1** indicates that a check pass is being
done,[/QUOTE]

When I disable the pass check it boots fine but I have to disable and then reenable the drive in order to get it to mount to the correct directory before that mounting to a tmp directory by default. I never touched sdb1 and have just let that alone.  It's sdb5 that's giving me the trouble.  If i have sdb5 have 1 or more passes it brings me to a command line screen with an error message saying it doesn't recognize /dev/sdb5 as a valied ext2 filesystem.  But when I do an e2fsck it says it's clean.  Then I do ctrl-D and it boots into the system fine, and also mounts sdb5 to /media/storage, the correct directory.

---

### Post by michaeljb2005 on 2006-06-28
Anyone?

---

