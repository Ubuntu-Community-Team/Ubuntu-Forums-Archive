---
title: "Installed but no GRUB appears"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by Tomatosoup on 2009-05-17
Hello,

This sucks big time:

I've got a Dell XPS 430 PC with a RAID-0 (striped) setting. Because of the RAID-0 setting I have to use the Alternate install CD, which does recognize my partitions.

So I installed using the Alternate install CD. Everything went fine. But after installation I just boot into Vista. No GRUB menu appears...

What the heck?!
It sucked already that I can't just use the graphical install CD, because of the RAID thing. But now it doesn't even work...

Why? And how can I fix this?

---

### Post by pi149 on 2009-05-17
This is exactly the same problem that I am having, but with XP.

---

### Post by Tomatosoup on 2009-05-17
> **pi149 said:**
> This is exactly the same problem that I am having, but with XP.

I see. This one: [http://ubuntuforums.org/showthread.php?t=1161611](http://ubuntuforums.org/showthread.php?t=1161611)
I hope there will be a solution. Sadly no solution yet...

---

### Post by pi149 on 2009-05-17
Hey, I got mine to work!  My computer had two drives so I just installed ubuntu on the other (non windows installed on) and set the boot order to boot the drive with ubuntu first.

---

### Post by Tomatosoup on 2009-05-17
> **pi149 said:**
> Hey, I got mine to work!  My computer had two drives so I just installed ubuntu on the other (non windows installed on) and set the boot order to boot the drive with ubuntu first.

Oh, okay. But I want to install it in a partition of my RAID-0 setting. And I still don't know how to accomplish that. GRUB doesn't seem to be installed.

Good luck though!

---

### Post by Tomatosoup on 2009-05-18
Anyone know of a solution?

---

### Post by ronparent on 2009-05-18
Your setup is also known as Fakeraid. Have you seen this site? 

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Also, is the raid0 your boot drive? If you post the output of this command from a terminal (from the live cd) we will have more information about your setup to work with.

sudo fdisk -l

Good luck.

---

### Post by Tomatosoup on 2009-05-18
> **ronparent said:**
> Your setup is also known as Fakeraid. Have you seen this site? 

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Also, is the raid0 your boot drive? If you post the output of this command from a terminal (from the live cd) we will have more information about your setup to work with.

sudo fdisk -l

Good luck.

Yes, I know I might have a FakeRaid (a bit condescending term by the way; don't mean you) setup. On that page you suggest they are mentioning RAID-5 but not RAID-0.

And why can't Ubuntu just install GRUB properly. I use the newest Ubuntu version, for God's sake...

I don't have access now to the computer with Ubuntu on it, albeit unusable.

But I can tell already:
I have two disks of the same size in a RAID-0 setup (as one disk).
I have a Primary NTFS partition with Windows on that disk (Bootable flag set).
I have an Extended partition with a Logical partition (ext3, mounted on "/", Bootable flag not set) and a partition used as swap-space.

Hope there's anyone out there who has the same problem and actually has a solution.

---

### Post by dstew on 2009-05-18
Grub is a fairly simple program. The boot loader in the MBR is just big enough to load the stage 2 program from the /boot/grub directory. Stage 2 understands all file systems, but cannot mount a RAID. So, you have to have stage 2 and the linux kernel that grub loads in an un-RAIDed boot partition. Once the linux kernel loads, it can mount the striped RAID.

I got around this by making a mirrored RAID for the /boot partition (RAID 1). Grub still cannot recognize it as a RAID, but because it is mirrored, grub can load the kernel without a problem. It just thinks it is a regular disk partition.

This refers to software RAID. You CAN install to grub to a striped FakeRAID, but it is difficult. See the [FakeRAID How-To]("https://help.ubuntu.com/community/FakeRaidHowto").

---

### Post by Tomatosoup on 2009-05-18
> **dstew said:**
> Grub is a fairly simple program. The boot loader in the MBR is just big enough to load the stage 2 program from the /boot/grub directory. Stage 2 understands all file systems, but cannot mount a RAID. So, you have to have stage 2 and the linux kernel that grub loads in an un-RAIDed boot partition. Once the linux kernel loads, it can mount the striped RAID.

I got around this by making a mirrored RAID for the /boot partition (RAID 1). Grub still cannot recognize it as a RAID, but because it is mirrored, grub can load the kernel without a problem. It just thinks it is a regular disk partition.

This refers to software RAID. You CAN install to grub to a striped FakeRAID, but it is difficult. See the [FakeRAID How-To]("https://help.ubuntu.com/community/FakeRaidHowto").

Still don't know how to install.
I see a lot of commands in the FakeRaidHowTo.
Why do they have to make it this hard?
Why not automate it?

---

### Post by dstew on 2009-05-18
FakeRAID support is not built into the Live CD or Alternate Install CD install programs. This is because of the limited size of the .iso, I believe. It would be an interesting project to try to create an automated FakeRaid installer. One could try writing a script to do what the FakeRaid How-To does.

---

### Post by Tomatosoup on 2009-05-19
> **dstew said:**
> FakeRAID support is not built into the Live CD or Alternate Install CD install programs. This is because of the limited size of the .iso, I believe. It would be an interesting project to try to create an automated FakeRaid installer. One could try writing a script to do what the FakeRaid How-To does.

The FakeRaid How-To doesn't mention RAID-0, only RAID-5.

Also, the Alternate CD does support my RAID-0 setting. Because it can see my two disks as one disk. Only it doesn't install GRUB correctly.

---

### Post by dstew on 2009-05-19
The Alternate Install CD is doing a software RAID. The FakeRaid How-To is for FakeRaid only. I think you could do a RAID 0 on a FakeRaid, if the controller supports it. The HowTo is only giving limited examples.

Grub will not work correctly on either a software RAID 0 or RAID 5. It will only work on a software RAID 1 (mirrored), or on an un-RAIDed partition. That is because the grub stage 2 boot loader which loads the Linux kernel cannot mount a RAID, only a plain file system. RAID 1 fools grub, because it is mirrored (2 or more identical partitions with identical file systems). Grub accesses one of the mirrored file systems without being aware that there is another.

---

### Post by Tomatosoup on 2009-05-21
> **dstew said:**
> The Alternate Install CD is doing a software RAID. The FakeRaid How-To is for FakeRaid only. I think you could do a RAID 0 on a FakeRaid, if the controller supports it. The HowTo is only giving limited examples.

Grub will not work correctly on either a software RAID 0 or RAID 5. It will only work on a software RAID 1 (mirrored), or on an un-RAIDed partition. That is because the grub stage 2 boot loader which loads the Linux kernel cannot mount a RAID, only a plain file system. RAID 1 fools grub, because it is mirrored (2 or more identical partitions with identical file systems). Grub accesses one of the mirrored file systems without being aware that there is another.

How come that Vista can boot then? It's installed in a partition within the RAID-0 setting.

And could I perhaps put something on my USB stick that will help boot from my hard drive?

---

### Post by dstew on 2009-05-21
Are you booting Vista with grub?

---

### Post by Tomatosoup on 2009-05-21
> **dstew said:**
> Are you booting Vista with grub?

No. But I wondered why Vista has a bootloader which does boot Vista and why I don't succeed in booting Linux.


But never mind:
I forgot I have an external hard drive and now installed Ubuntu 9.04 on that one. :)

Works okay. Had some problems with a 'restricted driver'. A driver ATI provided for its own line of graphics cards. And it seems I'm not the only one experiencing crashes at boot-up with garbled graphics.

But I found how to remove it:
sudo apt-get remove xorg-driver-fglrx

And I have succeeded in automatically mounting my RAID-0 drive(s). :)

Ubuntu 9.04 boots fast. :)

---

