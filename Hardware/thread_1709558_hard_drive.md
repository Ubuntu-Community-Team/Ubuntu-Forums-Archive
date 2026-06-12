---
title: "hard drive"
date: 2011-03-18
forum: Hardware
---

### Post by bob321 on 2011-03-18
hello,

I just bought a 3TB hard drive.
I'd like to configure it in order to be able to use it. From what I  understand it becomes more complicated for hard drives over 2TB.
I want to get the most out of it (being able to work with as many  operating systems as possible (including xp, for instance), being able  to boot on it, having if possible only one partition, etc...).
What am I supposed to do exactly?

Thanks

---

### Post by dabl on 2011-03-18
I would say, first step is to become a student of partitioning and partitioning tools.  I personally like Parted Magic (which uses GParted just like many others):

[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

The nice thing about using a Live CD or USB stick for partitioning is, you don't have to think about the requirement that target drives/partitions must be unmounted.

Then you need to remember that you are allowed a maximum of 4 primary partitions.  And also that Windows requires itself to be in a primary partition, but Linux does not.

Then you could study stuff like this:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[http://kubuntuforums.net/forums/index.php?topic=3090704.0](http://kubuntuforums.net/forums/index.php?topic=3090704.0)

[http://www.petri.co.il/the-ultimate-guide-to-hard-drive-partitioning.htm](http://www.petri.co.il/the-ultimate-guide-to-hard-drive-partitioning.htm)

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

Hope this helps.

---

### Post by bob321 on 2011-03-18
Well I can use the parted command line of ubuntu, I don't really mind.
My question is not really about the partitionning part, but rather about that issue regarding the 2TB limit.

---

### Post by dabl on 2011-03-18
This page has useful information, especially the table at the bottom:

[http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)

Note that you want the block size set to 2 or 4KiB.  I would assume your new drive comes with 4KiB blocks -- you can check that out.  If so, it will happily support a single 3T ext4 filesystem, if that's what you need.

---

### Post by bob321 on 2011-03-18
The limit is not set by the filesystem, but rather by the type of partitioning scheme that is applied.
I wouldn't be able to go into too much details, because I don't know them, otherwise I wouldn't be asking the question. But from what I understand, there's a 2TB limit that is embedded with mbr hard drives.
What are my options to bypass that limit ?

Thanks

---

### Post by fjgaude on 2011-03-18
> **bob321 said:**
> The limit is not set by the filesystem, but rather by the type of partitioning scheme that is applied.
I wouldn't be able to go into too much details, because I don't know them, otherwise I wouldn't be asking the question. But from what I understand, there's a 2TB limit that is embedded with mbr hard drives.
What are my options to bypass that limit ?

Thanks

You'll have to use the GPT partition system:

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

It's the coming thing for big drives. As I remember **gparted** can do the job on a new drive.

Another note: **fdisk** doesn't work with GPT partitioning, but **gdisk** does. And it's in the repositories.

---

### Post by oldfred on 2011-03-18
Do not use the gdisk in the repositories but download the newest verison. (I just used gparted but set it to gpt, not msdos.)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Windows will not boot from a gpt disk but will read NTFS partitions. Macs do a kludge to make it work to boot windows with gpt disks.

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Legacy BIOS issues with gpt
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

srs5694's to show 8 sector alignment post #9 new drives & SSDs
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by srs5694 on 2011-03-18
Oldfred has given you enough links to keep you reading on the topic for the next month! ;) I have a few more comments to add, though, and I might as well toss in one more link: I wrote [this article](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) about GPT and Linux a couple of years ago. It's still a good introduction, IMHO.

> **bob321 said:**
> I just bought a 3TB hard drive.
I'd like to configure it in order to be able to use it. From what I  understand it becomes more complicated for hard drives over 2TB.
I want to get the most out of it (being able to work with as many  operating systems as possible (including xp, for instance), being able  to boot on it, having if possible only one partition, etc...).

If you want to dual-boot Windows and Linux on the disk, your best bet is if you also have an EFI-capable motherboard. Some (perhaps most or even all) recent Intel boards have an EFI boot option, but it's disabled by default. You'll need a 64-bit version of Windows to boot in EFI mode, though. I'm not sure about booting FreeBSD or other OSes in EFI mode. Linux can be made to work, but through version 10.10, the Ubuntu installer doesn't work well with EFI. That's changing with 11.04; I've done successful installs in EFI mode with Ubuntu 11.04 alpha 2, without a lot of pain.

Note that your mullti-boot requirement is at odds with your single-partition requirement, unless you'd be satisfied with running one OS natively and everything else in a virtual machine. (That approach could also help with Windows on a GPT disk on a BIOS-based computer, of course.) I wouldn't recommend using a single partition on such a big disk, anyhow; I'd use separate root (/), /home, and swap partitions, at a minimum.

Another approach for multi-OS configuration is to use two disks. You can boot OSes that can't boot from GPT off of a smaller MBR disk. Some such OSes, such as Windows Vista and 7, can use a GPT data disk so long as they aren't asked to boot from it. (Note that only the 64-bit version of Windows XP can handle GPT disks, even as data disks.)

[quote=fjgaude]Another note: **fdisk** doesn't work with GPT partitioning, but **gdisk** does. And it's in the repositories. 	[/quote]

I realize oldfred's already said this, but I want to reiterate that you should *not* use the version of gdisk that's in the repositories, since it's so old. (It's version 0.5.1, IIRC, released in November of 2009, and the current version is 0.7.0, released about a week ago.) You can download version 0.7.0 [here](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.0/gdisk-binaries/) (note to readers in the future: go [here](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/) to find the latest version).

---

### Post by bob321 on 2011-03-18
Thanks to you experts for answering. I was feeling desperate.
So basically if I understood correctly, I have no choice but to use gpt as long as I want to use all 3TB ?
And if I choose gpt partitioning, not only will I not be able to boot on that disk, but I won't be able to use it with windows 32bits either ?
Is this correct ?
I use windows xp 32bits, so this is like a lose/lose choice :(. Either not use it with xp, or lose 33% of its price...
If I had known, I would never have bought such a shitty hard drive :(.

---

### Post by bob321 on 2011-03-19
Can someone answer the questions of the last post please ?
And I'd like to add this one: would xp 32 still not recognize a mbr disk if it is split in two 1.5TB mbr partitions ?
thanks

---

### Post by srs5694 on 2011-03-19
> **bob321 said:**
> Thanks to you experts for answering. I was feeling desperate.
So basically if I understood correctly, I have no choice but to use gpt as long as I want to use all 3TB ?

More-or-less. You could probably use the disk as a "raw" LVM physical volume. There are also [workarounds to push the 2 GiB limit of MBR,](http://www.rodsbooks.com/gdisk/workarounds.html) but I strongly recommend against using them. My brief test with this showed that Windows XP doesn't react well to this setup.

> And if I choose gpt partitioning, not only will I not be able to boot on that disk, but I won't be able to use it with windows 32bits either ?
Is this correct ?

No. Linux can boot from a GPT disk just fine, and Windows Vista and 7 can use a GPT disk as a non-boot disk. There's also the possibility of using a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to let Windows boot from the disk (but you'll have to be very careful about partition placement). Also, I have a sneaking suspicion that Windows XP will flake out on this disk even if you use a hybrid MBR on it, but I'm not positive of that.

> I use windows xp 32bits, so this is like a lose/lose choice :(. Either not use it with xp, or lose 33% of its price...
If I had known, I would never have bought such a shitty hard drive :(.

Put the blame where it belongs: With the OS. (Of course, Windows XP is close to a decade old, so I wouldn't cast all that much blame on it for not working with a technology that's ten years in its future.)

FWIW, my understanding is that many Windows XP drivers are built using 32-bit pointers for sectors, which means that they aren't likely to work very well with any disk with more than 2^32 sectors, no matter what partitioning system you use with it. (That's why I said XP might flake out with a hybrid MBR on this disk -- but I've never tested it, so I don't know that for sure.)

You could also consider upgrading Windows to something more recent or running XP in a virtual machine.

> Can someone answer the questions of the last post please ?
And I'd like to add this one: would xp 32 still not recognize a mbr disk if it is split in two 1.5TB mbr partitions ?

Don't be so impatient. The usual suggestion is to wait at least 24 hours before "bumping" a thread.

As to the question, my one test of the issue (using QEMU) suggests that Windows won't work in the configuration you specify.

---

### Post by bob321 on 2011-03-19
ok thanks

---

