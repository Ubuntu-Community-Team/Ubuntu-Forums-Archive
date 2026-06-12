---
title: "Ubuntu x64 (9.04) doesn't see hard drive"
date: 2009-09-12
forum: Hardware
---

### Post by M0st on 2009-09-12
I'm still quite a n00b, so I apologize for any missing information from this post...

I have been running Windows for a long time, and recently decided to try Ubuntu.  I installed Ubuntu on a fresh IDE hard drive, while keeping Windows on my main SATA drive.

The first few times I booted into Ubuntu, I was able to mount the SATA drive (but there were a few boots, where the drive didn't show up anywhere I could find).  I tried setting up the drive to Automount using NTFS Configuration Tool, and haven't seen the drive since.  I deactivated the Automount, but the drive still doesn't show up.

BIOS still sees the drive, and I can still boot into Windows with no problem, but I can no longer browse the drive when logged into Ubuntu.

On a possibly related note, the hard drive light in my case is constantly on now, when I'm logged into Ubuntu.  It still functions correctly in Windows, and from what I remember it worked ok when I could get the SATA to mount.

Any advice?  What other info can I provide to help track this issue down?

Thanks,
  -Mike

---

### Post by scragar on 2009-09-12
Try running mount. This will show your currently mounted drives and their locations:
```
mount
```

---

### Post by M0st on 2009-09-12
Thanks for the immediate reply!!!

here's the output:

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=mike)


...sorry I don't know how to make the neat 'code' box...

I'm expecting something like /dev/sdb2/ for the 2nd hard drive...

---

### Post by scragar on 2009-09-12
[noparse]```
Code in here
```[/noparse]

Yeah, it's not mounted at present, so let's make a directory for it and mount it, then we can add it to your fstab so it automounts in future.

First, the directory:```
sudo mkdir /media/Windows
```
Secondly, we find the windows partition:```
sudo fdisk -l | grep ntfs
```
This will spew out a line like:```
**/dev/sda1**               1          643   51340162   62  ntfs
```
The bit in bold is the part we want. Now we can add it to fstab so it automounts in future:
```
sudo su## become root for a little while
echo "**/dev/sda1** /media/Windows ntfs-3g defaults,allow_other,umask=0,users,nls=utf8,noexec 0 0" >> /etc/fstab
exit ##drop out of root
```
And finally we can just mount the drive now:
```
mount **/dev/sda1**
```

---

### Post by M0st on 2009-09-12
```
sudo fdisk -l | grep ntfs
```

returns nothing... it just puts another input line at the terminal

(in case it matters) it's a SATA drive with windows XP x64 (if that changes anything about how it may be formatted, since I'm guessing the '| grep ntfs' part filters the search results for NTFS formatted drives only...), but I still think it's formatted as ntfs...

...I'm thinking something went seriously awry somewhere...

---

### Post by scragar on 2009-09-12
Just drop the```
| grep ntfs
```Part, I don't have an NTFS drive to test on, it might be listed as something else(it just means you'll have to do a little searching :p).

---

### Post by M0st on 2009-09-12
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e4e17ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris



...and that's it :(

I've been scratching my head over this for a while... how do I find a drive I can't see...

---

### Post by running_rabbit07 on 2009-09-12
To make the code box just type [ code ]words[/code ] without the spaces.

---

### Post by M0st on 2009-09-12
thanks... I just wasn't sure if the output belonged in the code tags or not, since it's not something that should be input...

---

### Post by hal10000 on 2009-09-12
If fdisk can't recognize your sata disk, then something may be wrong with your sata subsystem.
run [COLOR="Red"]lspci[/COLOR] and look if you can find your SATA controller
Post the output here.

---

### Post by M0st on 2009-09-12
output from lspci:
```

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

```

it looks like there are 3 SATA controllers... maybe that's the problem?

---

