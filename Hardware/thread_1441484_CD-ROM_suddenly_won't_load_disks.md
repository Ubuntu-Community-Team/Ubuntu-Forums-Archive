---
title: "CD-ROM suddenly won't load disks"
date: 2010-03-28
forum: Hardware
---

### Post by kebo26 on 2010-03-28
Hi all:
New to the world of Linux, everything was going well on my new-refurbished T-60 when suddenly, in the middle of burning a series of iso images, my cd-rom just stopped working. No matter what I put in there, I get back "Unable to mount location: No media in drive." Additionally, I am now unable to mount a boot volume from startup!
I'm using 8.10 on a Lenovo T-60.

Here's the output of lshw -C disk:

*-cdrom                 
       description: DVD reader
       product: RW/DVD GCC-4247N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open

...and here's my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18056e88-b249-44a7-8457-ddd0e1abc36f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f6fdc30a-5013-4b96-b31b-dc59edf41664 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660 ,udf user,noauto,exec,utf8 0       0


Again, I'm really new to all this stuff, and have only includede the above 'cause people on threads like mine seem to get asked to post this stuff.

Thanx!

---

### Post by kebo26 on 2010-03-29
Bumpski!

---

### Post by khelben1979 on 2010-03-29
**File Manager - super user mode** can solve your problem if it's a permission trouble which have arisen.

Other than this, there could be a malfunction of the drive and then it needs to get replaced or repaired and it's got nothing to do with Ubuntu.

---

### Post by kebo26 on 2010-03-30
Oh-ho! A new development. Just tried a DVD and instead of failing to recognize that thre's anything in the drive at all, instead i get this error message:

 "[mntent]: line 9 in /etc/fstab is bad
  mount: can't find /media/cdrom0 in /etc/fstab or /etc/mtab "

So it would seem that there's something amiss with one of these two files. I tried swapping the udf and iso9600 arguments (options?) in the fstab file to no avail. Ennyways, here's my mtab file:

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-27-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/crichter/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,use$

Once again, any help in how I can fix these files will be rewarded with my eternal esteem.

Danke,

Corey Richter

---

### Post by anglican on 2010-03-30
> **kebo26 said:**
> 

...and here's my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18056e88-b249-44a7-8457-ddd0e1abc36f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f6fdc30a-5013-4b96-b31b-dc59edf41664 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660 ,udf user,noauto,exec,utf8 0       0



Then you got:

> 
"[mntent]: line 9 in /etc/fstab is bad
  mount: can't find /media/cdrom0 in /etc/fstab or /etc/mtab "
Look closely at your /etc/fstab file and you'll see that the file system type field in line 9 is incorrect, there is a stray space after iso9660 and before the ",udf". Remove it and see if it works OK.

H

---

### Post by kebo26 on 2010-04-02
Thanks for the suggestion, anglican, but no dice. I've dicovered that I can mount and view DVD's from the CL, but the computer still refuses to recognize when I've put in a CD or data disk. Rats!

Is there any way I can test my hardware from the CLI, like a way to see if the system's mis-IDed my drive or something?

Anyways, you guys are great and thanks in advance.

corey

---

### Post by khelben1979 on 2010-04-02
You can try to see if [Grip]("http://nostatic.org/grip/") is able to find your audio cd. Just install it by:

```
sudo apt-get install grip
```

Did it help?

---

### Post by anglican on 2010-04-02
> **kebo26 said:**
> Thanks for the suggestion, anglican, but no dice. I've dicovered that I can mount and view DVD's from the CL, but the computer still refuses to recognize when I've put in a CD or data disk. Rats!

Is there any way I can test my hardware from the CLI, like a way to see if the system's mis-IDed my drive or something?

Anyways, you guys are great and thanks in advance.

corey

When you say "no dice" do you mean that you get the same error message about an error in /etc/mtab or /etc/fstab? Which command(s) can you successfully use from the CL?

Perhaps udev is the problem. What's in your /etc/udev/rules.d/70-persistent-cd.rules? Could you also show us the tail of dmesg after inserting a disk.

H

---

### Post by tgalati4 on 2010-04-02
Could be a hardware problem.  The drives that Lenovo uses are not the best and fail with surprising regularity.

The DVD/CD drives have two laser LED's, one for DVD, one for CD.  So it's quite possible that the CD laser is toast.  Try a lot of different disks and see what works and what doesn't.

Post the output of:

cdrecord -checkdisk

If this was a refurbished unit, what sort of warranty does it have?

---

### Post by lorena.rangel on 2011-07-10
**I have not found a way to fix this, my dvd burner was working fine and then i suddenly got this error message when inserting a blank dvd, and now i can't get it to work:confused: can anyone please help me, i am totally new to linux:**

Unable to Mount UDF Volume
Error mounting: mount exited with exit code 1: helper failed with:
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


**this is my dmesg tail output**
lorena2011@LO:~$ dmesg | tail 
[ 3088.826691] udf: udf_read_inode(ino 71740) failed !bh
[ 3088.826700] udf: udf_read_inode(ino 71739) failed !bh
[ 3088.826707] UDF-fs: Failed to read VAT inode from the last recorded block (71742), retrying with the last block of the device (71743).
[ 3088.826717] udf: udf_read_inode(ino 71743) failed !bh
[ 3088.826725] udf: udf_read_inode(ino 71742) failed !bh
[ 3088.826732] udf: udf_read_inode(ino 71741) failed !bh
[ 3088.826740] udf: udf_read_inode(ino 71740) failed !bh
[ 3090.082346] UDF-fs: No anchor found
[ 3090.082355] UDF-fs: No partition found (1)
[ 3090.237636] ISOFS: Unable to identify CD-ROM format.
lorena2011@LO:~$

---

