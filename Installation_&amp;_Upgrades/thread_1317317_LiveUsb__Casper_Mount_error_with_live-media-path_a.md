---
title: "LiveUsb / Casper: Mount error with live-media-path and persistence; other related ?'s"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ziesemer on 2009-11-06
I've been having pretty good success creating a bootable USB flash drive with the Ubuntu "live" environment (casper).  I'm using the official release of Karmic Koala (9.10), x86, and have followed the notes at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) (method 3) and [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) .

The only real difference so far is that I plan on using Ext2 (or maybe even 3 or 4) instead of Fat16/32, and as such am using Grub2 (1.97) instead of SYSLINUX.  I'm also testing everything using VirtualBox, and as such, am using a virtual hard disk instead of an actual USB drive, as VirtualBox currently doesn't support booting from USB.

I had everything working great, including persistence.  However, the root of my boot drive seemed very messy, with 5+ folders created for the contents of the live CD (casper, preseed, etc.), another 5+ folders for persistence (etc, home, var, etc.), and everything else I was hoping to share the partition with.  Ideally, all of the contents of the live CD would be copied into a "ubuntu-live" directory, and all of the persistence data would be kept in a "ubuntu-persistence" directory.

Here is the Grub2 entry that I had when everything was working as expected:

```

menuentry "Ubuntu 9.10 32-bit - Live" {
	linux /casper/vmlinuz boot=casper persistent --
	initrd /casper/initrd.lz
}

```

I then moved all of the live CD folders (casper, preseed, etc.) into /ubuntu-live, and updated the Grub2 entry with the "live-media-path" option as documented at [http://manpages.ubuntu.com/manpages/karmic/man7/live-getty.7.html](http://manpages.ubuntu.com/manpages/karmic/man7/live-getty.7.html) :

```

menuentry "Ubuntu 9.10 32-bit - Live" {
	linux /ubuntu-live/casper/vmlinuz boot=casper live-media-path=/ubuntu-live/casper ignore_uuid persistent --
	initrd /ubuntu-live/casper/initrd.lz
}

```

I had to add the "ignore_uuid" option to prevent the boot from hanging with infinite "stdin: error 0" outputs (after "Begin: Running /scripts/casper-premount ...", 2 "Done." lines, and a few EXT4-4s kernel debug outputs, apparently due to the hidden ".disk" directory missing from the root of the drive.

However, I'm stuck with the following output: (OCR'd from VirtualBox print-screen using tesseract with manual edits)

```

[ 5.780380] device-mapper: dm-raid45: initialized v0.2594b
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
[ 6.937398] EXT4-fs (sda1): barriers enabled
Begin: Running /scripts/casper-premount ...
Done.
Done.
[ 6.939426] kjournald2 starting: pid 339, dev sda1:8, commit interval 5 seconds
[ 6.940156] EXT4-fs (sda1): delayed allocation enabled
[ 6.940575] EXT4-fs: file extents enabled
[ 6.941079] EXT4-fs: mballoc enabled
[ 6.941384] EXT4-fs (sda1): mounted filesystem with ordered data mode
[ 6.996176] aufs 2-standalone.tree-30-20090727
[ 7.167173] squashfs: version 4.0 (2009/01/31) Phillip Lougher
BusyBox u1.13.3 (Ubuntu 1:1.13.3-lubuntu?) built-in shell (ash)
Enter 'help&#8217; for a list of built-in commands.
(initramfs) mount: mounting /dev/sdal on /cow failed: Device or resource busy
Can not mount /dev/sdal on /cow

```

Hitting enter gives a "(initramfs)" BusyBox prompt.

Removing the "persistent" option allows for a successful boot as a normal live CD, but without persistence.

What does "cow" stand for in this context?

After some digging, this appears to be coming from line 426 in /initrd/scripts/casper , shortly after calling the "find_cow_device" function that is defined in casper-helpers.  Overall, it seems that something else already has /dev/sda1 locked, but I don't know what.  Not knowing exactly what "/cow" is supposed to be or what it is used for doesn't help, either.  I'm wondering if maybe this entire mount section is unnecessary, and if a symbolic link would suffice instead?

I considered trying to edit the casper script to make this work, or at least to add some additional debugging.  Is there an easier way to do this short of rebuilding it into a new casper/initrd.lz every time?  ([https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd))

Some additional references that I found:
[LIST]
[*] [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/406192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/406192)
"[karmic] various pre-mount errors".  Not sure this is even relevant.
[*] [http://brainstorm.ubuntu.com/idea/15173](http://brainstorm.ubuntu.com/idea/15173)
"Idea #15173: Add live-media-path boot option or similar, to allow booting from folder in root" Seems to be the exact same thing as I'm trying to do, though with no reference to the "live-media-path" option.
[*] [http://www.mail-archive.com/debian-live@lists.debian.org/msg00580.html](http://www.mail-archive.com/debian-live@lists.debian.org/msg00580.html)
"Re: "BOOT FAILED!" with a live-rw partition (ext2 and ext3 tested)" Same error that I'm getting, though reported at the Debian level.  Mentions a fix, but not sure if it would already be in Karmic or not.
[*] [http://bromavilleherald.com/index.php/Casper_boot_process](http://bromavilleherald.com/index.php/Casper_boot_process)
"Casper boot process"
[*] [http://manpages.ubuntu.com/manpages/karmic/en/man7/casper.7.html](http://manpages.ubuntu.com/manpages/karmic/en/man7/casper.7.html)
[*] [http://manpages.ubuntu.com/manpages/karmic/en/man8/initramfs-tools.8.html](http://manpages.ubuntu.com/manpages/karmic/en/man8/initramfs-tools.8.html)
[/LIST]

Finally, I also found [http://manpages.ubuntu.com/manpages/karmic/man7/live-getty.7.html](http://manpages.ubuntu.com/manpages/karmic/man7/live-getty.7.html) .  It mentions that it is a fork of Casper, and most significantly, includes a "persistent-path" option in addition to "live-media-path" and other potentially useful options.  Should I consider trying to switch over to this, instead, if even possible?

Are there any other ideas or fixes to get this working as expected?

Thanks!

---

### Post by ziesemer on 2009-11-07
Now I'm getting the exact same error, even without trying to move directories around.  I even tried re-creating everything from scratch, and am still getting the same "Can not mount /dev/sda1 on /cow" error.

Any help would be appreciated - thanks!

---

### Post by ziesemer on 2009-11-08
I thought that maybe this was an issue with Ext4.  Repeated the setup with Ext2 instead, but still having the same issue with persistence.  Can the Live files not share the same partition with persistence?  (Both on a partition labeled "casper-rw"?  Are 2 partitions required?)

---

### Post by ziesemer on 2009-11-08
This is looking related to [http://ubuntuforums.org/showthread.php?t=647844](http://ubuntuforums.org/showthread.php?t=647844) "Live USB with persistence in a single FAT partition", which appears to be written for 7.10 (Gutsy Gibbon).  Will have to see if the effort can be easily duplicated on Karmic.

---

### Post by ziesemer on 2009-11-15
I finally found the answer to one of my questions, which seems so obvious now!  COW: Copy-On-Write.  ( [http://en.wikipedia.org./wiki/Copy-on-write](http://en.wikipedia.org./wiki/Copy-on-write) , [http://wiki.debian.org/DebianLive/FAQ#Q.3AWhatis.2BAC8-cow.3F](http://wiki.debian.org/DebianLive/FAQ#Q.3AWhatis.2BAC8-cow.3F) )

---

### Post by ziesemer on 2009-12-18
Bump.  Can anyone please help me with this?  Thanks!

---

### Post by garvinrick4 on 2009-12-18
This is a working USB Flash drive with that operates with full Ubuntu O.S.
Has persistence for all 13 gig partition with boot in seperate partition done
with gparted manually. It works I am using it now on Laptop. 

I have finally got a 16 gig Flash drive to work as independent system. A lot of trial and error.
Used Live CD. 9.10 64 bit and the 16 gig flash drive.
Booted Live CD and selected install.
When it got to partitioning selected USB device of course.
1st partition was 500 meg ext3  /boot as mounting point
2nd partition was 13.5 gig ext3 / as mounting point
3rd partition was 2 gig Swap

IN THE 8TH PAGE YOU HAVE TO CLICK ADVANCED TAB AND SELECT BOOT AS THE SAME
AS YOUR 1ST PARTITION  THAT YOU SELECTED AS /BOOT AS MOUNTING POINT.

 Then add your repositories such as partners, medibuntu, backports, all the same ones as your normal install. You have over 12 gig left to work with so use what you want. Compiz works fine, the only thing in Karmic I have not gotten to work is sound and every install of 9.10 on my HP G71-34OUS has
had sound issues, I will get it. WIFI came right in. Has been a normal install.

Grub menu.  When you upgrade it installs itself onto your systems grub with no partition
number such as sba1 or any device. This works well it just installs a grub selection while
plugged in to USB port with recovery selection.

                  		  		  		 		 here is fdisk.   I am running flash drive now.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.7 GB, 16687038464 bytes
64 heads, 32 sectors/track, 15914 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0008849e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         954      976880   83  Linux
/dev/sdb2            3831       15914    12374016   83  Linux
/dev/sdb3             956        3830     2944000   82  Linux swap / Solaris

---

### Post by ziesemer on 2009-12-18
garvinrick4 - thanks for the reply!

However, it sounds like you're running the full Ubuntu OS, and not Casper?  I'd like to still use Casper if at all possible, to use the enhanced persistence options, and help avoid unnecessary writes to my flash drive.  This would also give me the option to run Casper with or without the persistent flag, just as 2 separate Grub entries.

---

