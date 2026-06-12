---
title: "Ubuntu 64 with RAID 5 install"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by tarkawebfoot on 2009-08-30
I'm trying to install Ubuntu 64 on a new build of an Asus P5Q Pro Turbo and an Intel Core 2 Quad processor.

I'm using the alternate CD, because I found three identical WD 120GB hard disks and set them up as a RAID 5 set with the Asus P5Q Pro Turbo MB I got, and the FakeRaid HowTo says the alternate CD has RAID 5 drivers built in.

The problem is when I run the install, it seems to work well until it reaches the disk partitioning part. It seems to detect and activate the RAID set with out trouble. However when the disk partitioning part comes up, my options are "Help with partitioning", a blank line that doesn't do anything, "Undo partitioning changes", and "Save and continue".

I cannot see anything to format. Am I just missing something, or is it just not detecting the RAID? It seemed to detect it when it asked if I wanted to activate the set???

I saw a posting about using the mdadm utility with the --assemble switch, but I thought I shouldn't need that with the alternate install.

Any ideas?

Thanx in advance,

Brian

---

### Post by tgrimley on 2009-08-31
be careful, mdadm and the motherboard raid are different things.  you'll probably have better support using mdadm and maybe better performance too (definitely better portability).

is there any data on your raid5 array or should it be blank / unformatted?

have you checked the individual disks?  whenever I've had problems with the installer it's been a bad disk.

---

### Post by ronparent on 2009-08-31
mdadm is a good choice if you intend to use only linux. If you plan to eventually dual boot with windows (any flavor) and need to access the raid from windows and linux, you would then have to use dmraid (otherwise known as fakeraid).

Apparently you intend to install ubuntu to the raid array. I am too usfamiliar with the alternate cd protocol to be much help to you. I can make some general comments. If you intend to switch to software raid you do need to turn off raid support in bios and erase any meta data already written to the drives before attemting to use mdadm and activating raid5 drives with it (ie **sudo dmraid -E**). Once you return the three disk to non-raid, straight SATA condition, you should then be able to create and assemble the software raid set.

Whichever way you go, once the raid drives are active, gparted would see the entire raid drive (incorporating all three disks) as unpartitioned space. The same should be true in the command line install with the alternate cd. At that point the basic choices should be to install ubuntu to occupy the entire raid drive, to use only part of the drive, or to manually decide the size and location of a partition to install to. The main thing you have to be carefule of is that the three disks may additionally show up as individual unpartitioned disks. To sucessfully install to raid stay away from those individual drives.

For fakeraid check this out: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

For software raid, this: [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

Installing ubuntu to raid of any flavor has pitfalla. Study the documentation and proceed systematically as advised. Its not too daunting when you know how to proceed, so do post any difficulties you run into.

---

### Post by tarkawebfoot on 2009-08-31
Hi again all,

Thanks for the replies.

I do not intend to run Windows, but I would like to boot from the RAID set. Also, all disks are clear of data; this is a fresh install.

I read both the Fake Raid HowTo and the Software Raid HowTo. It seemed like Fake Raid was easier since the setup was in the MB BIOS and the alternate CD is supposed to have drivers for booting from a RAID set. Apparently that's not true.

It would seem at this point that the mdadm route would be best choice. If that's the case, I shouldn't need the alternate CD, but since I've got it, I might as well continue using it.

BTW, checking the hard disks is a good idea. How can I do this during the install?

Thanx again,

Brian

---

### Post by tarkawebfoot on 2009-09-02
Ok,

I proceeded with the install, configuring software RAID 5. The install seemed to go as expected, but the system will not boot. It just sits with a flashing cursor after the POST phase. I notice that the Software RAID HowTo still says that the / and /boot file systems must be RAID 0 or 1 to be bootable.

It seems that fake RAID is the only way to make the system bootable from a RAID 5 set -- if that can even be done.

Now that there are partitions on each of the hard drives, the Fake RAID install may work. That's what I plan to try next.

But I wonder if it's possible to boot from a raid set at all at this point. If I can't boot from the raid set, is it possible to make a CD that just contains the kernel image and GRUB? I don't have a floppy for this system, and I'd rather have more reliable storage for the boot device anyway.

I really would like the entire system to be on the raid set; the whole point is that it can tolerate a disk crash. Recoverability is critical for this system.

I'd really like any input on ways to approach this if possible. Am I headed in the right direction with raid 5? If not, which way should I go?

Brian

---

### Post by tgrimley on 2009-09-02
Usually people who do this partition the disks where the first ~100-200MB  is a RAID 1 volume for /boot and the remainder of each hard disk is for the RAID 5 volume.

Or they use another drive for the system and mount /home on raid 5 and backup regularly.

---

### Post by miklcct on 2009-09-03
You can copy /boot/vmlinuz-* and /boot/initrd.img-* into another medium and use the appropiate method to make it bootable (isolinux for iso filesystems, syslinux for vfat filesystems), and run the whole system from RAID 5

---

### Post by tarkawebfoot on 2009-09-16
So I tried re-configuring the hardware RAID after doing an install to see if having the disks partitioned made any difference. It made none. Ubuntu does not recognize the RAID set.

So now I've re-installed with software RAID and I'm back to where I was at the last post. Everything is set up, but I can't boot the RAID 5 set. I wanted to switch over to a virtual terminal to get the contents of /boot as mentioned in the last post and burn it to a boot CD, but I also notice virtual terminals aren't working. Is this normal with the Alternate CD install?

Is there another way to boot just long enough to make a boot CD?

Does anyone know if I'd have better luck with Fedora or Open SUSE?

Thanx again

Brian

---

### Post by tgrimley on 2009-09-16
Pretty sure linux will not boot from a raid5 volume.  

Here's is some gentoo docs on setting things up:  [http://en.gentoo-wiki.com/wiki/Software_RAID_Install](http://en.gentoo-wiki.com/wiki/Software_RAID_Install)

---

### Post by tarkawebfoot on 2009-09-17
Ok, I got it.

I partitioned each of my three drives into two spaces. One 0.5 GB partition and one 119.5 GB partition. I then setup the three small partitions in a RAID 1 set housing /boot, with a spare, and the three large partitions in a RAID 5 set.

I can now boot from the disks and still have full redundancy. I'm currently configuring my new system.

The only quirky part was that after doing the initial partitions, the multiple partitions did not appear in the 'Create MD Device' section. After rebooting, they did however.

Thanks for the help,

Brian

---

