---
title: "Cloning disk, grub doesn't boot"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by afilonov on 2009-05-19
I tried to clone my hardy installation today, have a problem.

I used gparted live CD (v.0.4.4.1) to copy partitions from old disk to the new one. Boot partition was moved as is, root partition (/) was resized. Trying to boot from the new disk, no action whatsoever. No grub, no grub errors, nothing, just a blinking cursor. I tried to reinstall grub into mbr, grub returns success, but still no boot. New disk has a "bootable" flag on the /boot partition. Reinstalled grub several times. Checked UUIDs, they are the same on old and new disks. And yes, I disconnected the old disk when trying to boot from the new one.

When booted from live CD, I can mount partitions, can read and write.

Hardware details:

Dell 400SC, 1.1G of RAM.

Old disk: 40G original, supplied with the computer
New disk: 160G Western Digital. Similar disk is used successfully on another computer, although I used different cloning procedure there (mondo).

Can't boot from BIOS, can't boot from hardy live CD, when choosing option "boot from the hard disk".

OS: Ubuntu Hardy, with all latest updates.

Any ideas?

---

### Post by Vrekk on 2009-05-19
It sounds to me like while the /boot got copied, the MBR did not.  This link might help you make a new working one.  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) that should help you get it back and running like new!

---

### Post by logos34 on 2009-05-19
> **Vrekk said:**
> It sounds to me like while the /boot got copied, the MBR did not.  This link might help you make a new working one.  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) that should help you get it back and running like new!

I thought he did that already:

> **afilonov said:**
> I tried to reinstall grub into mbr, grub returns success, but still no boot. New disk has a "bootable" flag on the /boot partition. Reinstalled grub several times. 

afilanov, did you enter reinstall grub as described in Vrekk's link?

Could you post output of

sudo fdisk -l

---

### Post by Vrekk on 2009-05-19
> **logos34 said:**
> I thought he did that already:

Opps i didnt see that he already did that. My bad

---

### Post by logos34 on 2009-05-19
> **Vrekk said:**
> Opps i didnt see that he already did that. My bad

unless I'm mistaken, sounds like he ran it from the grub-shell ('success')...wonder why his grub menu isn't coming up, hmm...

---

### Post by afilonov on 2009-05-19
> **logos34 said:**
> I thought he did that already:



afilanov, did you enter reinstall grub as described in Vrekk's link?

Could you post output of

sudo fdisk -l


Yes, I reinstalled grub from grub-shell, when booted from live CD.

I ran the following commands:

find /grub/stage1

(response: (hd0,0))

root (hd0,0)

setup (hd0)

response from setup command was normal (it's not the first time I'm installing grub).

I'll post fdisk -l results in couple of days. This computer is in use a lot of time, can't touch it now.

---

### Post by zurcherart on 2009-05-31
I'm in exactly the same situation as the original poster. 

Any new advice on solving this problem?

My hardware (ASUS) and disk partiiton size are different, but otherwise my scenario and and situation is the same as the original poster's.

I cloned one drive to a new drive.  Removed the old drive (it seems to be failing slowly so this is a data recovery attempt).  Verified the data on the new drive is sound (using efsk).   I installed the new drive in the place of the old drive.  UUIDs match. 

I try to boot.

The startup hangs right at the point where Grub should print it's "loading message"--there is no feedback on the screen.

When I thought that the MBR might be missing I used grub install just like the OP above.

Finally, I installed Jaunty in the remaining free space in this machine.  The jaunty install recognized that Hardy was already installed and according to the messages displayed updated/reinstalled the MBR and set it up to offer a choice between booting Jaunty and Hardy.  

I restart the machine.  I think now I can simply choose Hardy rather than Jaunty and everything is will be recovered.

No. Everything hangs up on Grub as before.

Please any suggestions to get this working?  Murphy's law.  I need this machine for freelance work and every minute I spend trying to resolve this is time I'm not finishing my critical freelance project and the deadline is Tuesday.  

Here is the outout from fdisk on that machine (taken with the jaunty live cd):
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00048028

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30022   241151683+  83  Linux
/dev/sda2           59719       60801     8699197+   5  Extended
/dev/sda3           45321       59718   115651935   83  Linux
/dev/sda4           30023       45320   122881185   83  Linux
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris
/dev/sda6           59719       60022     2441817   83  Linux
/dev/sda7           60023       60044      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075672

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

AFAIK
/dev/sda1 is the cloned hardy that didn't boot before
/dev/sda4 is a partition where version control repositories are stored
/dev/sda3 is a partition I mount from Virtual machines when i run them
/dev/sda2 is the new partition created in the jaunty install
/dev/sda6 is the jaunty install that still doesn't work

---

### Post by afilonov on 2009-06-02
Posting output of fdisk -l:

root@ubuntu:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e43ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          65      522081   83  Linux
/dev/sda2              66       14088   112639747+  83  Linux
/dev/sda3           18547       18938     3148740   82  Linux swap / Solaris
/dev/sda4           18939       19457     4168867+  82  Linux swap / Solaris

This output is from session using my Hardy (8.04.2) live CD.

I have a bad suspicion that BIOS (Dell BIOS revision A04) doesn't recognize drive properly. However, it shows correct size (160GB). I made one more attempt and made root partition smaller than 120G, didn't help a bit.

---

### Post by logos34 on 2009-06-02
> **afilonov said:**
> Posting output of fdisk -l:

root@ubuntu:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e43ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          65      522081   83  Linux
/dev/sda2              66       14088   112639747+  83  Linux
/dev/sda3           18547       18938     3148740   82  Linux swap / Solaris
/dev/sda4           18939       19457     4168867+  82  Linux swap / Solaris

This output is from session using my Hardy (8.04.2) live CD.

I have a bad suspicion that BIOS (Dell BIOS revision A04) doesn't recognize drive properly. However, it shows correct size (160GB). I made one more attempt and made root partition smaller than 120G, didn't help a bit.

strange.  no idea why you're not even getting a grub error (it can't even read the mbr?)

just a stab in the dark: you might try cloning it a second time, but use Clonezilla "device-to-device" option (whole disk).  This will copy the entire thing over (mbr incl.) in one shot.

---

