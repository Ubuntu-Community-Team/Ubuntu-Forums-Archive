---
title: "WD 500gb passport will not mount (or do anything)"
date: 2009-12-01
forum: Hardware
---

### Post by afabisze on 2009-12-01
Yesterday I bought a 500gb WD My Passport.  The first time I plugged it in, it automatically mounted and I was able to put some movies on there.

Today, however, I can't get it to do anything.  When I plug it via usb, it makes some noise and the blue light continuously blinks.  There is no icon that shows up, and I can't find any sign of it being connected and/or recognized by my computer.

I don't know if any of this from the terminal helps (this is while the device is plugged in)...I am running 9.10

alexander@alexander-laptop:~$ sudo fdisk -l

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14928   119909128+  83  Linux
/dev/sda3           14929       15566     5124735    5  Extended
/dev/sda5           14929       15566     5124703+  82  Linux swap / Solaris
alexander@alexander-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4113a30d-c633-4b64-807d-f2a42b5935f3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a44bd94e-abfc-4092-81a1-c0112084704f none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
alexander@alexander-laptop:~$ sudo blkid
/dev/sda1: UUID="4113a30d-c633-4b64-807d-f2a42b5935f3" TYPE="ext3" 
/dev/sda5: UUID="a44bd94e-abfc-4092-81a1-c0112084704f" TYPE="swap" 
alexander@alexander-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alexander/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alexander)

---

### Post by teward on 2009-12-01
can you do me a favor?

Go to gparted (partition editor) and tell me if it shows up under the device list.  If it does, what does it show?  If it doesn't, then I believe it to be a problem with hardware.

---

### Post by afabisze on 2009-12-01
it did not show up under the device list in gparted...so you think something must be wrong with the device itself?

---

### Post by afabisze on 2009-12-02
The wd passport did not work on a mac either, but a kingston usb drive was automatically recognized on my computer, so i think you are right in saying that the hardware has some flaw.

does any one have any ideas on something i should try before returning it?

---

### Post by teward on 2009-12-02
Well, if I were there, I have the software to see if the device's  Input/Output system failed or not.  But since I'm not there, I don't believe there's much you can do.  If it doesn't work in more than one system, then the drive is screwed/dead/bad/failed/<insert synonym for any of the previous words here>.

---

