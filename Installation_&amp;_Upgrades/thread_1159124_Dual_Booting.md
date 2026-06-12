---
title: "Dual Booting"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by Narusegawa on 2009-05-14
I'm thinkig about dual booting Vista and Ubuntu. I have 2 physical SATA Drives and 1 IDE.

I was tempted bythe following:

Creating a 1gb partition BEFORE the Vista one for /boot

/sda1 1gb     /boot
/sda2 89gb    NTFS (Vista)
/sdb1 150gb   NTFS (Games)
/sdb2 50gb    /
/ide1 80gb    NTFS (Music)

The above is what I was thinking of doing, and in the unlikely scenario that /sdb2 is wiped, erased, formatted then I won't lose grub. Just wondering if that'd work? I tried Gentoo ages ago, didn't like it, but then I formatted the drive it screwed my system. I had to dig out a restore CD to get Vista booting again. I don't wanna risk that again, hence the idea behind /boot

Who knows, I might like Ubuntu, I might decide to try a few distro's before I settle on one I like, my main point is I don't want to have to keep re-installing GRUB over and over and over again to keep a working system.

---

### Post by logos34 on 2009-05-14
You don't even need a /boot...If you're paranoid about losing / accidentally, try a [dedicated grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"), just big enough (a few MBs) to hold your grub boot files (i.e. menu.lst)

Either that or make a [grub boot floppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy") or [bootable grub cd]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html").  Or simply burn a **Super Grub Disk CD **(link below), which can boot windows

hope that helps

---

### Post by Narusegawa on 2009-05-15
Oh right... I've just always had a /boot swap and /, it's just how I was taught to install linux many years ago. To be honest I just made a /boot lastnight of 1gb in size (allowing for many kernels), but frankly hard drive spaces nowadays aren't an issue. :)

I ended up putting it all on /sdb as I realized moving the vista partition from the first partition of /sda would've caused vista BCD a ton of issues. I'll just keep the /boot if I don't like ubuntu anyway, but so far looks nice. Installed smoothly, no hiccups, got my nvidia driver prompted to download... I'm impressed with the end-user setup approach.

Just need to work out a solution to allow me to remote control from the office now, I use LogMeIn but that doesn't have a linux port of it :(

---

