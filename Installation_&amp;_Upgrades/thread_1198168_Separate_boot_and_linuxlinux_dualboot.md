---
title: "Separate /boot and linux/linux dualboot"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by rrcs on 2009-06-27
Hello.

I'm trying to educate myself about the necessity of a separate /boot partition, but different sites say different things. I get the impression from some sites, that it is not as necessary as it once was. Opinions on this?

Related: I would like to try out other Linux distros in dualboot with Ubuntu. If you recommend a separate /boot, can this be shared between distros, or should each distro have its separate /boot (I'd run out of primary partitions soon, though, as I understand /boot needs to be a primary partition)?

Or would it in the case of Linux/Linux[/Linux/…] be advisable not to have separate /boot partitions? (I plan for them to share /home.*)

Thank you in advance for help/opinions :D

*ETA: Or maybe not, as I read further. I'll figure out file sharing separately, then, just have the questions on whether separate/shared /boot is advisable.

---

### Post by Herman on 2009-06-27
> I'm trying to educate myself about the necessity of a separate /boot partition, but different sites say different things. I get the impression from some sites, that it is not as necessary as it once was. Opinions on this?In the old days, (well, not all that long ago really), hard discs were very small and often when a hard disk in an old computer failed, or just when larger hard disks became available, many people upgraded old computers with larger hard disks than their motherboard's BIOS could address. 
During boot-up, the boot loader needs to be able to give the BIOS directions to the Linux kernel in order for the BIOS to load it. If the kernel is allowed to be written to just any random location on the hard disk, it might be placed somewhere out of range of the co-ordinates that the old BIOS could map. In that case the computer wouldn't be able to boot. With GRUB, the user would be given an Error 18 message.
A BIOS update might fix that problem, but if no more recent BIOS updates are available, the next best thing to do is make a separate /boot partition. The kernels are housed in the /boot partition, and if the /boot partition is located at or close to the start of the hard disk, it effectively 'fences' the kernel in, and any new kernels that may be added during an update. Once the kernel is booted, the kernel contains the drivers to address the rest of the hard disk, so it can 'see' all the operating system files and data further out on the disc. There are still a few old computers like that still working, but they're getting pretty rare now, and are about ready for retirement to a computer museum. (LOL).
One or two valid reasons still exist for a separate /boot partition though, you may need a separate /boot partition if you plan on installing Ubuntu with an encrypted root file system, or if you have a few hard disks and you want to set up a RAID array, or LVM. 
If you don't have any special reason for a separate /boot, it's not advisable to bother with one. You can do it just for fun, but it will only use up a little of your disk space, and take up a partition number unnecessarily. Otherwise it won't do any real harm, but it'll be no help either.
> Related: I would like to try out other Linux distros in dualboot with Ubuntu. If you recommend a separate /boot, can this be shared between distros, or should each distro have its separate /boot (I'd run out of primary partitions soon, though, as I understand /boot needs to be a primary partition)?For Linux it doesn't make any difference at all whether the /boot partition is primary or logical. 
You cannot (easily) share a separate /boot between Linux distros because both distros will fight over the menu.lst file. 
I have helped people after the fact, to create a second menu.lst with an alternative name and edit the upate-grub script of one distro accordingly, but that's not something you really want to be bothered with, it's just extra work for no gain, and afterwards you'll be stuck with a funny configuration 
It's much easier just to have a standard installation. 
A shared /boot partition is not what you would want if you're planning on dual booting or multi-booting Linux, if you can possibly avoid it.
> Or would it in the case of Linux/Linux[/Linux/&#8230;] be advisable not to have separate /boot partitions? (I plan for them to share /home.)At least each distro should have it's own separate /boot, if you really want to use separate /boot partitions.
I would advise against the idea unless you have a special reason such as an encrypted root file system.

---

### Post by Herman on 2009-06-27
Something that might be a better idea for dual or multi booting Linux distros would be a 'Dedicated GRUB Partition'.
Probably a 'Dedicated GRUB Partition' is what you really want.

A lot of people don't know the difference between a 'Separate /boot Partition' and a 'Dedicated GRUB Partition'. Even many website authors don't understand the meanings of some of the terms they like to use.
Both kinds of partitions may contain GRUB, but not necessarily. A 'Separate /boot Partition' might instead contain LiLo or some other boot loader.
A 'Separate /boot Partition' is owned by an operating system and is registered in the operating system's /etc/fstab file as the operating system's /boot partition.
A 'Dedicated GRUB Partition' is good for dual and multi-booting Linux as it  'operating system independant', and is not part of any operating system. GRUB is actually a mini operating system itself. It can take commands and give feedback.
If you have a 'Dedicated GRUB Partition' and you delete a distro you won't lose your ability to boot any/all of your other operating systems. 
A 'Dedicated GRUB Partition' only contains GRUB files and no Linux kernels or initrd.img files, so a 'Dedicated GRUB Partition' doesn't take up very much hard disk real estate at all.  
[How to make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_").-  contains only GRUB, no other files  are required.

Regards, Herman :)

---

### Post by Spalmore on 2009-06-27
As [Herman]("http://ubuntuforums.org/member.php?u=31861") was saying a Primary Grub boot partition might be the best idea. Then I would use chain loader to load the grub of the other OSs. This lets each OS have it's own kernel list with out messing any thing up for the other OSs. Also using chain loader means that you don't have to manually edit the grub each time that one of the OSs updates it's kernel.

---

### Post by Herman on 2009-06-27
> Then I would use chain loader to load the grub of the other OSs. This lets each OS have it's own kernel list with out messing any thing up for the other OSs. Also using chain loader means that you don't have to manually edit the grub each time that one of the OSs updates it's kernel.
 +1 :)
> As [Herman]("http://ubuntuforums.org/member.php?u=31861") was saying a Primary Grub boot partition might be the best idea.
+1, I agree, . . . only I still think it's totally irrelevant whether your /boot partition or 'Dedicated GRUB Partition' happens to be primary or logical.

That idea probably has a lot to do with Window's observance of the partition table's 'boot flag', but I'm only guessing. 
There's an old ms-dos convention about having a 'boot flag' set for booting a primary partition. 
According to this old convention should be exactly one boot flag in every MBR, otherwise some BIOSes will throw up an error message and refuse to boot any partition in the hard disk. There can be between one and four 'primary' partitions in the partition table, and only one of those is allowed to have the boot flag at any time. The 'boot flag' is supposed to 'mark the partition as 'active', and even if there's no boot loader IPL code in the boot loader area of the partition table, the BIOS is supposed to 'see' the boot flag and jump to the first primary partition that has been 'marked active', (with the boot flag), and try to boot it by the boot sector, (the first sector of the partition).

The boot flag can easily be moved with GRUB's 'makeactive' command.
We always (traditionally) use the 'makeactive' command in every menu.lst boot entry for any Windows operating system. I'm not sure if that's still needed today, I have been told that many computers BIOSes can boot modern Windows systems regardless of the position of the boot flag in the partition table. I'm not sure.

I do know that the boot flag is not necessary for booting Linux, but I think some BIOSes still require a boot flag somewhere in a partition table or they might overlook that hard disk and skip to another disk, or throw an error.

I also know that it is possible to use a partition editor to set the boot flag in a logical partition, and boot Windows in a logical partition.
When we do that, we need to delete the 'makeactive' command from GRUB's menu.lst otherwise GRUB will error out. GRUB can't set a boot flag in a logical partition.

One thing that made GRUB useful to users of old Windows systems was it's ability to 'hide' and 'unhide' Windows installations in primary partitions.
That made it possible to dual boot more than one Windows, and have them all installed in primary partitions, so they retain their boot loaders and remain independant of one another. The default Microsoft dual boot rule is for the newer Windows to give up it's boot loader to the older Windows in the primary 'boot partition', and be installed in a logical partition. That way, if the older system has a virus, you lose both operating systems instead of only one.
I can't understand what Microsoft could have been thinking when they came up with that idea, maybe they have a lot of shares in the antivirus companies. 
Anyway, they still persist with it even in these modern times. Actually, they got worse! Modern Windows operating systems are designed so that they'll still do that even if the other Windows is 'hidden', and even if it's on a different hard disk.
In any case, I think the term 'primary boot partition' is a Microsoft Windows term.

So there are three kinds of 'boot partition': a primary boot partition - for Windows, a 'Separate /boot Partition' - belonging to a Linux operating system, and a 'Dedicated GRUB Partition', which is operating system independant.

The name 'Dedicated GRUB Partition' was possibly coined by Mr Steve Litt, who wrote the excellent web page following, link: [Making a Dedicated Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm").
I think it's a good idea to use Steve Litt's name for a 'Dedicated GRUB Partition' as opposed to a 'Separate /boot Partition' so readers can understand what we're writing about. Same with a Microsoft 'primary boot partition'.

I don't know if there's any formal organization that meets and haggles out computer words and terms and decides what they're supposed to mean.
Differences in the way we use computer words and terms can certainly cause some confusion and misunderstandings though, and even lead up to somebody 'borking' their computer! In particular the ambiguity in the way some writers use the term 'boot sector' interchangeably with the term 'master boot record'.
By 'borking' their computer I mean making it temporarily unbootable by the normal method.

Well, enough of a rant from a would-be language cop, LOL, let's just have fun with Linux! 

Regards, Herman :)

---

