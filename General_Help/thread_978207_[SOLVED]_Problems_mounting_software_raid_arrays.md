---
title: "[SOLVED] Problems mounting software raid arrays"
date: 2008-11-10
forum: General Help
---

### Post by pssturges on 2008-11-10
Hi,

I have 2 software raid arrays on my mythbuntu backend system. The first is a raid1 with 2x500gb sata hdds formatted as ext3, as /dev/md0 mounted as /storage. The second is raid0 1x200gb + 1x300gb formatted as xfs, as /dev/md1 mounted at /recordedtv.

I have had this problem for several months since the arrays were installed under hardy. Under hardy, the system would hang during boot until the reset button was pressed. Generally about 1 in three boots would be successful. Once a successfull boot was achieved, the system would function normally, with the raid arrays correctly mounted.

Now under intrepid, the system boots successfully each time, but approximately 50% of the time the raid arrays are not mounted. In this case if I do: "sudo mount -a", I get:

```

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: /dev/md1: can't read superblock
ntfs-3g: Failed to access volume '/dev/sdf1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

```

dmesg | tail:
```

[  334.356047] ppdev0: unregistered pardevice
[  941.979997] EXT3-fs: unable to read superblock
[  941.981151] XFS: SB read failed
[ 1165.415084] __ratelimit: 15 callbacks suppressed
[ 1165.415091] xfs_db[7007]: segfault at 28 ip b7f349f0 sp bfd882c4 error 4 in libpthread-2.8.90.so[b7f2d000+15000]
[ 1165.543210] xfs_db[7023]: segfault at 28 ip b80469f0 sp bfd99bd4 error 4 in libpthread-2.8.90.so[b803f000+15000]
[ 1201.467375] xfs_db[7069]: segfault at 28 ip b7ef09f0 sp bfd41b84 error 4 in libpthread-2.8.90.so[b7ee9000+15000]
[ 1202.225998] xfs_db[7094]: segfault at 28 ip b7f579f0 sp bffa95f4 error 4 in libpthread-2.8.90.so[b7f50000+15000]
[ 1295.094549] EXT3-fs: unable to read superblock
[ 1295.095179] XFS: SB read failed

```

My fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=920490ae-e8c7-401d-a9c0-2ab054a39383  /otherpart  ext3  suid,dev,defaults,exec,relatime  0  1
# /dev/hda3
UUID=841eb7cf-cb40-400f-8117-506bb9f99b6f /      ext3    defaults,relatime        0       2
# /dev/sdb1
# /dev/sda1
#UUID=904b7759-b8f2-4cb1-b177-aa6ca6bbffb2  /storage  ext3  suid,dev,exec  0  2
# /dev/hda5
UUID=62d5e529-6dbd-4b47-b4f9-023420de209c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#UUID=904b7759-b8f2-4cb1-b177-aa6ca6bbffb2  /storage  ext3  suid,dev,exec  0  0
/dev/md0  /storage  ext3  suid,dev,exec,relatime  0  0
/dev/md1  /recordedtv  xfs  suid,dev,exec  0  0
/dev/sde2  swap  swap  defaults  0  0
/dev/sdf1  /portable  ntfs  user,suid,uid=1000,dev,gid=1001,exec  0  0

```

Any help much appreciated,
Phil

---

### Post by fjgaude on 2008-11-11
I'm confused... you are mounting two different devices at /storage, sda1 and md0?

---

### Post by pssturges on 2008-11-11
Sorry if it's not clear. I guess your looking at my fstab? The line with sda1 was used to mount a single hdd before I installed the raid arrays. That line is now commented out. That hdd is now part of the raid1 array mounted at /recordedtv. I hope that clarifies things. 

Cheers
Phil

---

### Post by fjgaude on 2008-11-12
Hard to say what could be causes this... You might try putting this line in:

```
gksudo /usr/share/initramfs-tools/init
```   # to stop a race condition with md

   157 maybe_break mount
   158 sleep 5
   159 log_begin_msg "Mounting root file system..."
```


sudo /usr/sbin/update-initramfs -uk all
```    # run to rebuild the image

Make sure you put the sleep line in the "mount" paragraph.

Let us know what happens.

---

### Post by pssturges on 2008-11-12
Thanks for the reply. Now i'm a little confused. Did you want me to run:
```

gksudo /usr/share/initramfs-tools/init

```in a terminal? 

When I do so I get:
```

gksudo /usr/share/initramfs-tools/init
Loading, please wait...
mount: according to mtab, sysfs is already mounted on /sys
mount: proc already mounted
/usr/share/initramfs-tools/init: line 24: /conf/arch.conf: No such file or directory
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

```
Or did you want me to edit /usr/share/initramfs-tools/init and add the extra lines?

Thanks
Phil

---

### Post by fjgaude on 2008-11-12
Edit the file; sorry I left out the **gedit** in the gksudo line:

```
gksudo gedit /usr/share/initramfs-tools/init
```

Add the sleep line as indicated in the above post.

---

### Post by pssturges on 2008-11-12
Well, I tried that and it looked promising. 3 consecutive successful reboots where everything mounted correctly. But the 4th time the raid arrays did not mount. Do you think increasing the sleep time is likely to help?

Thanks again.
Phil

---

### Post by fjgaude on 2008-11-13
Try it... some have used 10 seconds... depends on your setup and its speed.

---

### Post by pssturges on 2008-11-13
Tried 10 & 15. Still the same result.

My very basic understanding of what is going on here is that early on in the boot process the raid arrays should be configured/initialized/assembled, whatever. At some point later, as long as that process is complete and successful, then the arrays are mounted in the file system. In my case, the arrays are sometimes not being successfully initialized. As I can't even mount the arrays manually after boot, it seems that the initializing process is failing for some reason.

So, I guess I need to work out where and why it's failing, and then work out how to fix it or work around it. A possible work around may be to have a second attempt at initializing after the first fails, maybe?

Problem is, I have no idea where to look. Is there a log I should be looking at?

Cheers
Phil

---

### Post by fjgaude on 2008-11-13
You can look over the log files in System/Administration/System Log menu.

Wish I knew exactly what to suggest... you are booting the system off a separate drive from the two arrays, eh?

How did it go when you made the raid1 array with two dissimilar drives?

It seems that both hardy and intrepid have few issues when it comes to software raid under **md**, which is managed under **mdadm**.

One thing you could try is to re-name your **/etc/mdadm/mdadm.conf** file (or simply delect it), remove mdadm, re-boot. Then re-install mdadm and then run this command:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be auto-generated and everything should be mounting correctly.

Let us know how things go.

---

### Post by pssturges on 2008-11-13
> **fjgaude said:**
> 

One thing you could try is to re-name your **/etc/mdadm/mdadm.conf** file (or simply delect it), remove mdadm, re-boot. The re-install mdadm and then run this command:

```
sudo --assemble --scan
```

A new mdadm.conf file will be auto generated and everything should be mounting correctly.


Yep, that seems to have done it! I'm up to about 9 or 10 reboots, and all successful!

Just a few notes.
```
sudo --assemble --scan
```
Should be:
```
sudo mdadm --assemble --scan
```

> **fjgaude said:**
> 
you are booting the system off a separate drive from the two arrays, eh?


Yes

> **fjgaude said:**
> 
How did it go when you made the raid1 array with two dissimilar drives?


Oops! Got my raid levels mixed up in the original post. Have edited accordingly.

Many thanks Frank. Your help is very much appreciated. I'm so glad to get this problem sorted out after living with it for several months!

Cheers
Phil

---

### Post by fjgaude on 2008-11-14
Thanks for correcting my omission of mdadm! I'm sure things wouldn't work that way but you got the point.

Glad you fixed the assemble issue, but we still don't know what it was that caused it to begin with. The contents of the mdadm.conf file could have had somethnig not-right in it but now all is okay there. If you saved the original you might compare if there are differences and let us know.

If you have things that are important to you on a raid0 array please have a backup made... it's just a matter ot time before something happens and you will lose that data. I have three: one online, another near-line, and the last, as off-line. <smile>

---

