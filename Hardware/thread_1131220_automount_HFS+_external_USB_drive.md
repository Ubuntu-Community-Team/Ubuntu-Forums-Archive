---
title: "automount HFS+ external USB drive"
date: 2009-04-20
forum: Hardware
---

### Post by svenole on 2009-04-20
I've got an external USB drive that I use to backup both my ubuntu laptop and an iMac. Therefore I've laid out a HFSplus filesystem on the drive and turned off journaling (using the iMac) to make it writeable on the ubuntu system. This works fine for me with a couple of hickups:

1. I have to make sure that the USB-disk is not connected to the ubuntu-laptop under boot due to the fact that an fsck procedure will screw up the journal setting. 

2. Automount of the HFSplus filesystem to /media/USB-DISK does not work when the disk is connected to the laptop after boot. It worked for a long time, but now it does not work anymore and I am not able to find out why. 

My question to this forum is if someone knows how to fix this second issue. The disk is perfectly mountable in rw mode if done manually:

mount /dev/sdb -t hfsplus /dev/sdb /mnt

# fdisk -l 
Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2677f40

   Device Boot      Start         End      Blocks   Id  System

---

### Post by uncoolbob on 2009-04-26
I am getting exactly the same thing!  (It was working maybe a few weeks ago.)  Something must have broken with an update.

When I mount manually (without even the -t option) it works perfectly.

> cat /etc/mtab
/dev/sdb1 /tmp/usb hfsplus rw 0 0


When the desktop provides the error
"Invalid mount option when attempting to mount the volume 'External USB HD'."
there's nothing informative in /var/log/messages - where else to look?

my system:

Ubuntu 8.10
Linux home 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux

---

### Post by KhurramM on 2009-04-26
Try ntfs-config

Hope this solves your problem.

---

### Post by uncoolbob on 2009-05-04
thanks for the suggestion, but actually there's no ntfs-config on my system

and the strange thing is that this USB HD mounts perfectly (automatically) when logged in under another account (one I set up for my daughter to use tuxpaint etc).

that suggested something in a dotfile or another preference/setting but I've looked and can't find what could be wrong.

My account didn't have "mount user space filesystems" privileges, so I gave myself that and logged back in again - still no luck.

any ideas?

---

### Post by uncoolbob on 2009-06-20
I realised that even though it does mount under the unprivileged user account, it's readonly.

I Googled some more and found a thread on here saying that you have to disable journaling (do that on the Mac in Disk Utility and some ninja option key holding).  Tried that and it still didn't work.   So I have reformatted the USB drive in hfsplus ("Mac OS Extended") non journaled and non case sensitive (just to be sure) and it mounts straight away read/write in Ubuntu.

I guess the kernel has found a journal, even though it isn't active, and is disabling write perms.

---

### Post by uncoolbob on 2009-06-21
Still more followup...

I found today that this non-journaled hfsplus USB drive was mounting readonly again (even though /etc/mtab says rw).

More Googling... and it seems that maybe the filesystem is corrupted (perhaps when it was mounted on the Mac).  I installed "hfsprogs" which provides fsck for hfsplus, so after:

sudo fsck.hfsplus /dev/sdb1

The drive mounted read-write properly.

---

### Post by medicineuk on 2009-06-22
hi uncoolbob I have been struggling with this same problem.

It seems that the hfs drive has to be unmounted cleanly to get read/ write access. My drive mounts read/ write most the time but then if linux crashes for whatever reason it becomes read only again. The only way I have found to get back full read/ write access is to plug the Hardrive in to Mac and the eject it, this cleans up the mount and Linux is happy again.

It's pretty annoying and I would love to find away that I can clean up the mount within Linux so I didn't have to get my Mac all the time.

---

### Post by uncoolbob on 2009-06-22
have you tried fsck.hfsplus?  (install "hfsprogs" first)

I only ran it once and it seemed to do the trick, even though it didn't report any errors that it had to clean up.

I'll report back when I know more.

---

### Post by stesosaso on 2010-02-26
Hi, 

I have the same problem, I am unable to write to my HFS+ usb drive.

here is what gives me df -h :
```
saks@saks-studio:/$ df -h
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sdc5              19G  6,5G   12G  36% /
udev                 1007M  412K 1006M   1% /dev
none                 1007M  624K 1006M   1% /dev/shm
none                 1007M  336K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sdc1              21G  9,5G   11G  48% /media/5E6491756491509F
/dev/sdb1             917G   65G  806G   8% /media/DATA
/dev/sda1             459G  203G  233G  47% /home
/dev/sr0              1,5G  1,5G     0 100% /media/cdrom0
/dev/sde3             466G   40G  426G   9% /media/LaCie II

```The concerned drive is /dev/sde3...
Does anyone have the solution?

What i'd like to happen is that when I connect one of my different HFS+ extrenal usb drives, the rw property is on for me and all other accounts on my karmic Koala.

Please excuse my English as it is not my mother language
Thanks in advance for your appreciated help

---

### Post by uncoolbob on 2010-02-26
At the moment I have to do this (I have not looked into fixing the problem for months though).

1. Unmount drive from GUI.

2. % sudo fsck.hfsplus /dev/xyz

3. Remount drive from GUI.

4. Write to disk.

**...every time...**

I could create a hook to do this before every mount, that would be nice.

---

### Post by djhomeless on 2010-07-15
> **uncoolbob said:**
> Still more followup...

sudo fsck.hfsplus /dev/sdb1

The drive mounted read-write properly.

Hey uncoolbob. Just wanted to say thanks as this solved my problem. My media server unfortunately frequently loses power (my significant other keeps turning off the power strip to save the planet - heh) so whenever it comes back up, the disk would mount ro. Thanks to this tip, I don't have to haul my mbp just to fix the disk. 

Thanks!

---

