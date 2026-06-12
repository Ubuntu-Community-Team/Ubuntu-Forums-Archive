---
title: "USB Disk/External Drive Mounting Problem"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by timegateuk on 2007-05-10
Hello All,

I have feisty fawn installed on my pc which is working fine except for one anoying thing. When i plug in a USB memory stick or my external media player/hard drive they don't auto mount (these did auto mount when i had edgy eft installed). I can use gnome partition editor to check the drive is recognised and i can manually mount it which causing another issue. When i manually mount them i only have read access.

Can anybody help with this?

Thanks

---

### Post by Nemo Omnibus on 2007-08-20
> **timegateuk said:**
> Hello All,

I have feisty fawn installed on my pc which is working fine except for one anoying thing. When i plug in a USB memory stick or my external media player/hard drive they don't auto mount (these did auto mount when i had edgy eft installed). I can use gnome partition editor to check the drive is recognised and i can manually mount it which causing another issue. When i manually mount them i only have read access.

Can anybody help with this?

Thanks

Hi,

I have the same issue - has anyone fixed this yet?

Rgrds,

Nemo

---

### Post by Helskov on 2007-08-20
Hi 

Mine has worked but 2 weeks ago it just stopped working. 
Its a hell mounting it manually. 
Anyone with a solution?

---

### Post by louca on 2007-08-21
Same problem here. My usb dvd drive auto mounts fine but the hard drive is not cooperating.

I haven't used ubuntu in a while, what was the code to mount with read/write access?

---

### Post by umdmariachi on 2007-08-21
I'm having the same problem and all the solutions i've found only give me read access. I have two usb thumb sticks that mount fine but my 120 gig seagate external won't. results of fdisk -l are:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7872     2015216    e  W95 FAT16 (LBA)

Disk /dev/sdd: 1014 MB, 1014497280 bytes
17 heads, 32 sectors/track, 3642 cylinders
Units = cylinders of 544 * 512 = 278528 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3643      990704    6  FAT16

---

### Post by umdmariachi on 2007-08-25
has anyone gotten any help with this issue?

---

### Post by cdrom600 on 2007-08-25
It seems like enough people have problems with automounting that if someone knowledgeable could write a troubleshooting guide, it would be a big help.

---

### Post by merlinus on 2007-08-25
@[COLOR=Black][umdmariachi]("http://ubuntuforums.org/member.php?u=229638")

From sudo fdisk -l, looks like you have a boot flag set on sdb4, which is an empty partition.  You might want to get rid of it.

Also, post output of

```

mount
cat /etc/fstab

```

-merlin
[/COLOR]

---

### Post by plug-jsync on 2007-08-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/86292](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/86292) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I did some hunting around, since I have encountered the same problem on roughly 30+ systems running Feisty over the past couple months.  It seems there is a very real and legitimate bug in the gnome-volume-manager (possibly related to interactions with the NetworkManager specific to Ubuntu).  There's a launchpad bug opened [**here**]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/86292") , but I don't see any resolution, and it's been open for quite a while.

For those who need instructions to get the device mounted while we wait for the next release of Ubuntu to, perhaps, fix the problem, the steps below may help.
> 
Open a terminal window (usually Applications | Accessories | Terminal)
type ls /dev/sd*
plug in your USB device, wait about 15 seconds
type ls /dev/sd*
Look for a new item in the list (let's assume /dev/sdg and /dev/sdg1 are new)
remember the new item(s) that end in a NUMBER, that's what you put in place of sdg1 below.
type pmount /dev/sdg1 usbdisk1
The usbdisk1 is a label, and you can use something else if you like
the drive should now be mounted at /media/usbdisk1 (or whatever you entered for the label) and should also show up on your desktop.
When you're done with the drive, you should right-click and select "Unmount Volume" before unplugging it.

Hope that helps.

---

### Post by cdrom600 on 2007-08-26
It looks like this: [https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices) may eventually develop into a useful reference.

---

### Post by umdmariachi on 2007-08-27
@Merlin

 mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdd1 on /media/disk-1 type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower)
/dev/sdb1 on /media/usbdrive type vfat (rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)


cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=7c6eb2f3-8993-4976-ba1d-f77709fb0e61 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=d0071269-ad4d-0c8c-1e0e-5a494024b43f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

@plug-jsync
Thanks for the help there, at least I can now store and edit files on there.

---

### Post by merlinus on 2007-08-27
mount shows the drive.  Follow info here for adding it to /etc/fstab:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

-merlin

---

### Post by umdmariachi on 2007-08-30
Thanks a lot for your help Merlin, Its working great now.

---

### Post by merlinus on 2007-08-30
Excellent, and continued good luck!

-merlin

---

### Post by umdmariachi on 2007-08-30
Ok, I spoke too soon! I restarted my machine and it did not auto mount. I'm trying to go back and see what I did wrong but any more help would be greatly appreciated.

---

### Post by umdmariachi on 2007-08-30
I went back and repeated the steps and got it working again. I checked the /etc/fstab and it seemed allright. I dunno what the problem is.

---

### Post by dpm on 2007-09-08
It might not apply to anyone, but the reason my USB stick wouldn't automount was what's mentioned on this bug comment:

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/438](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488/comments/438)

Note: this only applies to Feisty.

Cheers.

---

### Post by umdmariachi on 2007-09-08
mine works if i type sudo mount -a in the terminal when i start.

---

