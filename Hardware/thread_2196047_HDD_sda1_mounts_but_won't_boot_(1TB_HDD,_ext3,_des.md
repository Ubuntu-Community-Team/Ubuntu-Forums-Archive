---
title: "HDD sda1 mounts but won't boot (1TB HDD, ext3, desktop)"
date: 2013-12-27
forum: Hardware
---

### Post by watchpocket on 2013-12-27
Greetings folks,

 I'm suddenly having big problems booting my System76 Wild Dog desktop  unit.  When I try to boot up, all I see is text flying by, way too fast  to read. This continues until I press the front-panel "reset" button.

After hitting "reset," I've plugged in a live-USB flashdrive with a  bootable Ubuntu-12.04 on it, and have been booting from that.  (Using  this flashdrive is the only way I've been able to boot over the last few  days.)

"Disk Utility" on the flashdrive's Ubuntu, when I run that utility's  "SMART Data -- View SMART data and run self-tests,"  says that my  1-terabyte, ext3-formatted HDD has[COLOR=#0000ff]*** 362 bad sectors***[/COLOR]. (I don't know how serious that is or isn't.)  It also has a red warning at ID #5 "**[COLOR=#ff0000]Reallocated Sector Count[/COLOR]**" where at right, it shows (in red) "[COLOR=#ff0000]Normalized: 92, Worst: 92, Threshold 36, Value: 362 sectors[/COLOR]".

When I run Disk Utility's "Check Filesystem," it reports: "File system  check on '15 GB Filesystem' (Partition 1 of ATA ST31000528AS) completed.   File system is clean."

When I boot with the live-USB ([COLOR=#008000]/dev/sdb[/COLOR]), I can mount both the [COLOR=#b22222]root ( / )[/COLOR] and [COLOR=#b22222]/home[/COLOR] partitions of the disk ([COLOR=#008000]/dev/sda[/COLOR]), and I can open and look at the files in both those partitions.  (The disk has a [COLOR=#800080]15GB root[/COLOR] partition, an[COLOR=#800080] 8GB swapspace [/COLOR]partition and a [COLOR=#800080]/home[/COLOR] partition that takes up the rest of the [COLOR=#800080]900-some GBs[/COLOR]  on the disk.  I'm running Ubuntu 9.10 (Karmic) on this disk drive and  want to get the drive to boot so I can fresh-install 12.04.3 LTS on it.)

  At some point a few days ago I ran a terminal command (I forget which  one) and got "The superblock could not be read" error message.  So I  went through the steps described here:  [https://linuxexpresso.wordpress.com/...ock-in-ubuntu/]("https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")

After running:

*sudo mke2fs -n /dev/sda1*

I was shown nine different superblock backup numbers, and after running

[I]sudo e2fsck -b <backup-number> /dev/sda1
[/I]
on all nine of them (9 times, same command, different #), nothing had changed.  

In other words every time I tried to re-boot without the flashdrive  plugged in, I saw the GRUB menu first, then, below an Ubuntu logo, a  thermometer bar moves left-right, left-right for a full minute or so,  then the busybox-type black screen with the white text flying by. 

I have a boot-repair report here:  [http://paste.ubuntu.com/6632700/](http://paste.ubuntu.com/6632700/)

[SIZE=2]**My question is, whether this is a superblock issue or not,** **how can I repair the disk so I can boot from it again?**
[/SIZE]
*Thanks!*

---

### Post by sisco311 on 2013-12-27
duplicate: [http://ubuntuforums.org/showthread.php?t=2195861](http://ubuntuforums.org/showthread.php?t=2195861)

[s]Thread closed.[/s]

---

### Post by Iowan on 2013-12-28
Moved to Hardware.

---

### Post by fred-lorrain on 2013-12-28
I would stop trying to recover that drive and create an image (which can be done from System>Disks>copy or a bootable Acronis cd or similar) to a new HDD, boot from installation media, and do a repair install if it is offered as an option. Sounds like the bad blocks are all at beginning of the drive, which are preventing the repair. When doing a repair install go for the " I know a bit about the problem" option and choose bootloader, that will probably get you going again.

---

### Post by watchpocket on 2013-12-29
Thank you for the response.  I've actually decided to unplug (at least for now) the old, corrupt HDD, install a brand new identical replacement drive (just arrived today), plug the same power & data plugs that were connected to the old drive into the new one, fire up gparted and format the new drive the same as the old (15 GB root; 8 GB swap; the rest as /home).  

The only change in formatting I'll make is that the old drive used the ext3 filesystem, I see no reason not to use ext4 for the new one. My Sys76 box is 4 years old but I don't think that should create any problems with using ext4.  I am, however, going to leave the BIOS firmware in place, I think, and not try to mess with UEFI.  (It's doubtful I'd know what I was doing by trying to make a change like that on older hardware.)

I'm putting ubuntu 12.0.4.3 onto a USB stick right now so that I can boot from that and then install it onto the new drive.  (The live-USB I'm booting from now is an older 12.04; I'd prefer to install the current dot-three updated version.)

Then later, I'll move most of the files over from the old to the new.  

At that point I'm a little unsure about how to connect the old one as a 2nd drive and make the old one a /dev/sdb or /dev/sdc or whatever, where to go to do that (only in gparted or other places like /etc/fstab too?)   and if I need to modify things like /etc/fstab entries and so on, how to make sure the two drives play nice & make it so the old one doesn't try to boot (remove its boot flag in gparted?).  

askubuntu.com has been a help, also [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) 

I'm new to installing & partitioning drives & have never updated or installed an Ubuntu (or any other) OS.  However, I've been reading a lot over the last few days and I'm thinking it should go okay.  (I'm sure I'll be back here if it doesn't.)  

At any rate, I hope this sounds like a moderately prudent course of action.

---

### Post by watchpocket on 2013-12-30
Replaced the drive, partitioned it, installed 12.04.3, all, amazingly, without a hitch.

---

