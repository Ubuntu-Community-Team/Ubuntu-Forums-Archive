---
title: "USB HDD not mounting when hot plugged NTFS"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by Leon945 on 2007-09-07
Hello.
I recently installed Ubuntu and upgraded to Ubuntu Studio.
I had all my updates done.. added a couple of programssss... was on my way to the linux lifestyle when suddenly...
BAM!
Banshee decided it was time to end my journey.
I was scanning my External USB NTFS 160GB HDD, with banshee and froze on a song (ironically by rage against the machine), so i did what any run of the mill linux newbie would, i FORCED QUIT Banshee's butt...

Afterwards, before a reboot of any kind, I decided it was good time to install NTFS-3G for Write support.
Synaptics does its magic, i restart... and 
BAM #2
My USB external HDD did not mount.
I enabled NTFS write support for both internal and external devices.
Internal worked fine but external still would not show.

I tried mounting it manually to no avail, sudo kept yelling at me saying: "You have to run ntfsfix", so I did.
ntfsfix /dev/sda4 (which is the instruction sudo gave me).
It said it had been processed successfully and that I had to reboot to windows twice to get it to work.

I didnt because i dont have windows installed on this pc.
So i forced mounted the External drive with an instruction i was given by Ubuntu, (i dont quite remember it)

It worked, but i was afraid some damage could be done to my data, so i unmounted immediately.
I was adviced in this forum, that the best thing to do was to get to a windows machine, because they suspected a dirty partition and said windows would "checkdisk its butt" out of the way.

So I did, I got into windows with my HDD plugged in and powered, nothing out of the ordinary happened... And i was able to access it from windows no problem at all.

I rebooted, still hardrive plugged in (to windows) and same deal...
Everything looked fine and dandy.

So i decided to get back to ubuntu.
I boot ubuntu and to my not so unexpected lack of surprise, my HDD is not automatically mounted.

I tried manually mounting by doing 
sudo mount /dev/sda4
but it tells me the device is not found in fstab
I tried editing the fstab to add the device and mount point, but it tells me (when i try to mount manually) that the device does not exist.

I the procedeed to back up on my own steps, and uninstalled ntfs-3g write support.
But nothing happened, again to my not unexpected lack of surprise.

So here I am, frustration setting in borderline depressionistic, considering making a clean reinstall of Ubuntu (an idea which i dreadfully dread).

I would be eternally grateful to whom may have a solution to my bump in the ubuntu journey.

Thank you in adance to anyone who might have read this extensive post.
Trully yours,
Borderline Suicidal Ubuntu User.

---

### Post by Phurious on 2007-09-07
You could try something a little different.  Instead of mounting by device name, connect your USB drive, open terminal and run:

```
blkid
```

This should spit out the UUIDs for all of your drives.  Armed with this knowledge, try editing your FSTAB with the UUID for the USB drive (take the hyphens out of the UUID):

UUID=<UUID> <MNT LOCATION> ntfs-3g defaults,locale=en_US.utf8 0 0

Save the FSTAB and run:

```
sudo umount -a
```

Then:

```
sudo mount -a
```

See if anything changes.

---

### Post by Leon945 on 2007-09-08
Thank you for your help...

It almost worked! but no...
I re-installed the ntfs-3g because i saw you put it in the filesystem type.

I did the "blkid" command and at first it did show my external drive (no UUID) with /dev/sda4.
I created an entry in fstab

/dev/sda4 /media/EXTERNAL ntfs-3g defaults,locale=en_US.UTF-8 0 0

i then did

sudo umount -a
and proceeded with
sudo mount -a

it told me that there was a problem with the partition, and that i had to run chkdsk and reboot twice on windows.

I did it, i ran chkdsk and rebooted twice, i the "safely removed" the HDD from windows and plugged it in to UBUNTU.
I had a terminal open, and i got this bunch of messges, and i dont know what they mean.
```
rod@rod-desktop:~$ 
Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] Oops: 0000 [#1]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] PREEMPT SMP 

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] CPU:    0

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] EIP:    0060:[make_class_name+53/160]    Tainted: P      VLI

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] EFLAGS: 00010202   (2.6.20-16-lowlatency #2)

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] EIP is at make_class_name+0x35/0xa0

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] eax: 00000000   ebx: ffffffff   ecx: ffffffff   edx: 0000000b

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] esi: f88e8d91   edi: 00000000   ebp: 00000000   esp: df9a7e40

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] Process khubd (pid: 2129, ti=df9a6000 task=dffbb570 task.ti=df9a6000)

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] Stack: f38a9e24 f88fb20c f38a9e1c f38a9e24 f88fb180 c025c561 00000000 f88fb214 

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]        f38a9e1c f6b43000 00000213 ffffffed c025c5e8 f38a9c00 f88e2b50 f38a9c00 

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]        f6b43000 f88e01bb f6b43038 f6b43000 f88da8a5 f6b43324 f7efee18 f956dec0 

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] Call Trace:

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [class_device_del+161/288] class_device_del+0xa1/0x120

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [class_device_unregister+8/16] class_device_unregister+0x8/0x10

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f88e01bb>] scsi_forget_host+0x4b/0x60 [scsi_mod]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f88da8a5>] scsi_remove_host+0x55/0xe0 [scsi_mod]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f955fc7e>] storage_disconnect+0xe/0x20 [usb_storage]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f8885d00>] usb_unbind_interface+0x50/0xa0 [usbcore]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [__device_release_driver+107/160] __device_release_driver+0x6b/0xa0

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [device_release_driver+30/64] device_release_driver+0x1e/0x40

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [bus_remove_device+95/144] bus_remove_device+0x5f/0x90

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [device_del+349/448] device_del+0x15d/0x1c0

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f88e2b50>] __scsi_remove_device+0x30/0x80 [scsi_mod]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f88831be>] usb_disable_device+0x7e/0xe0 [usbcore]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f887f596>] usb_disconnect+0x96/0x120 [usbcore]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f88802d8>] hub_thread+0x248/0xc30 [usbcore]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [schedule+873/2704] __sched_text_start+0x369/0xa90

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [<f8880090>] hub_thread+0x0/0xc30 [usbcore]

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [kthread+0/240] kthread+0x0/0xf0

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000]  =======================

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] Code: ff ff 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 c6 89 7c 24 0c 89 c7 89 e8 89 14 24 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 38 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 f8 91 f1 ff ba f4 

Message from syslogd@rod-desktop at Sat Sep  8 04:19:39 2007 ...
rod-desktop kernel: [30837.464000] EIP: [make_class_name+53/160] make_class_name+0x35/0xa0 SS:ESP 0068:df9a7e40

```

i tried runnning
blkid
again, but now it never showed the /dev/sda4 device.
so now, i can't mount it of course.

help anyone?
thank you in advance.


---------------------------------------------------
I rebooted ubuntu and 
blkid
once again showed me the device
```
rod@rod-desktop:~$ blkid
/dev/hda1: UUID="71839b80-131f-4c23-8584-ee94a8d89407" TYPE="reiserfs" 
/dev/hda2: UUID="38be4860-3072-4386-bd24-78ec83ec1e17" TYPE="swap" 
/dev/hda3: UUID="46E0-A72C" TYPE="vfat" 
/dev/sda4: TYPE="ntfs" 
```

sudo umount -a
and
sudo mount -a

and i got the message saying i should do the chkdsk again
```

rod@rod-desktop:~$ sudo mount -a
Failed to read $UpCase, unexpected length (65536 != 131072).
Failed to mount '/dev/sda4': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

```

I did, and while doing the chkdsk /f i rebooted ubuntu, just in case.
After the two boots on windows i plugged it back in ubunut, but i get the same thing when trying to mount.
That i have to do the chdsk. which i JUST did.

This is my fstab at the moment:
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/hda1 / reiserfs notail 0 1
/dev/hda3 /media/HDD ntfs-3g defaults,locale=en_US.UTF-8 0 0
# Entry for /dev/hda2 :
UUID=38be4860-3072-4386-bd24-78ec83ec1e17 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda4 /media/EXTERNAL ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Like i said, i installed the ntfs-3g from the ubuntu repos.

thannk you for your help-.

---

### Post by merlinus on 2007-09-08
You might post output of:

```

sudo fdiisk -l

```

-merlin

---

### Post by Leon945 on 2007-09-08
merlinus, thanks for your help, i decided to post a new thread since it's now about hardware...

anyway...
for some reason ubuntu is not listing my external drive anymore.. here is the output of
blkid
and
sudo fdisk -l

```
rod@rod-desktop:~$ blkid
/dev/hda1: UUID="71839b80-131f-4c23-8584-ee94a8d89407" TYPE="reiserfs" 
/dev/hda2: UUID="38be4860-3072-4386-bd24-78ec83ec1e17" TYPE="swap" 
/dev/hda3: UUID="46E0-A72C" TYPE="vfat" 
rod@rod-desktop:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8510    68356543+  83  Linux
/dev/hda2            8511        8759     2000092+  82  Linux swap / Solaris
/dev/hda3            8760       30401   173839365    7  HPFS/NTFS
rod@rod-desktop:~$ 

```

i got the error again, the long one on my last post, the kernel whatever messages.
umm...

what COULD be going on?

---

### Post by merlinus on 2007-09-08
Unless you always leave the external plugged in, you do not need an entry in /etc/fstab.  It should automatically mount, and if you have ntfs-3g installed, give write privileges.

Another strange thing, though, is that

blkid

sees hda3 as vfat rather than ntfs.

Go through all of the settings and preferences for removable media to make sure the correct boxes are ticked.

Also, run 

```

sudo ntfs-config

```

and make sure the appropriate boxes are ticked, and then restart.

-merlin

---

### Post by Leon945 on 2007-09-10
sorry fellas..
i decided i was taking longer to solve this thing than it would take me to simply reinstall ubuntu.

So i reinstalled ubuntu, and everything is ok now...

thanks alot for your help.

---

