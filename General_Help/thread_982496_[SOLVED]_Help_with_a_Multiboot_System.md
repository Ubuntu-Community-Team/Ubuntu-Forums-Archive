---
title: "[SOLVED] Help with a Multiboot System"
date: 2008-11-14
forum: General Help
---

### Post by GepettoBR on 2008-11-14
I have just (finally) bought a new computer, which should arrive next Friday, and it has quite a huge hard drive; so I decided I'd try out some other OSes besides Windows and Ubuntu, to learn more about how they (and computers in general) work. Thanks to StumbleUpon, I ran into this page a few months ago: [[link](http://www.justlinux.com/forum/showthread.php?threadid=147959)]

I intend to install Windows XP, 3+ flavors of Linux, including Ubuntu (my main OS) and one BSD (I'm leaning towards FreeBSD) following the guidelines in the linked thread.

I know that I need to install XP in a primary partition and that Linux distros (and GRUB itself) will play nicely in logical partitions, however the reading I have done on dual-booting BSD and Linux has confused me to no end, and I can't begin to imagine if it will conflict with Windows in any way as well. This whole deal with slices inside partitions and partitions inside slices (since the authors of the articles I read hadn't apparently agreed on a terminological standard) seems to me very confusing, especially a bit about not having a BSD partition before a Linux partition, or having to hide partitions or not nesting Linux and BSD logical partitions in the same extended partition. I *think* it all boils down to hiding the Linux partitions when booting BSD and vice-versa. Again, I don't know how Windows feels about all this, and Windows does have monopolistic tendencies over the hard drive.

I will do all the partitioning from GPartEd in a LiveCD and my data will only be moved to the new machine once I'm done installing everything, to avoid the risk of accidentally wiping it out during one of the many installations.

Thus, and having in mind that disk space is not a problem (my data will be on a separate (500GB) disk from the OSes, so I have 250GB to play with), I ask of the Ubuntu community:

a)What size should the GRUB-only partition be if I want it to be big enough to house GRUB2 when the stable version finally gets released? 

b)What filesystem would be best for the GRUB partition, and why?

c)Even though GRUB will work well from a primary or logical partition, would there be any advantage or disadvantage to either?*

d)Since Ubuntu will be my main OS, would there be any advantage or disadvantage in installing it to a primary partition instead of a logical partition?*

e)Should *BSD go to a primary partition or a logical partition?*

f)With what filesystem should I format the *BSD partition, or should I allow the *BSD installer to format it for me?

g)Will *BSD be able to share my swap partition with the Linux distros, will it require its own swap partition or does it use another virtual memory method (like Windows' paging file)?

h)With an initial 2GB of RAM and every intention to buy more, what is a reasonable amount of swap space for this configuration?

i)I doubt my swap partition will be used at all (I only want one to be on the safe side) but just in case: is it better to place it on the same disk as my OSes, or on the same disk as my data?

j)I have read about the possibility of a previously installed OS not being able to find the swap partition if a posterior installation formats it, but I have not found a way to solve this. If this does happen, is the fix a simple matter of editing /etc/fstab?

*I kept them separate because the questions came to me in different moments, but these three can be simplified to "What are the differences between a logical partition and a primary partition?", apart from the limit of 4 physical partitions in a disk.

This is unrelated to the threads main topic, but to avoid starting another thread with very little relevance:
[list]
[*]Suggestions for Linux distros to try out would be appreciated (I'll definitely install Gentoo and Arch, was also thinking about Slackware and gOS, not sure, though). I would rather the OS have an x64 version, but it's not necessary. Since I'm doing this as a learning experience, I'd also like the OSes to differ somewhat from each other in a way that is noticeable to me, the end-user/administrator, and not just in under-the-hood aspects. Comparing Gentoo's portage system to Ubuntu's .deb packages is a nice example of what I mean. Different Desktop Environments by default are also a plus (right now, I seem to have only GNOME and KDE covered).
[*]Suggestions regarding which BSD flavor to install are also appreciated.
[*]In fact, just about anything can be suggested. I don't think I'll try Solaris, but other than that everything is game. My greatest problem is not knowing about my options.
[*]This computer will connect to the Internet via a wireless router. For the installation processes, should I temporarily move it to the router's location and connect via a wire, or is a network-less installation fine (my wireless adaptor is not supported OOTB by the current Linux kernel versions)? 
[*]Will there likely be problems with X if I use a different monitor during installation than the one I'll actually use (otherwise I'll have to drag my TV across the house as well...)?
[*]Assuming I have the same version of X in every distro, can I take one of the xorg.conf files and copy/symlink it into all of them for easier management?
[*]500GB is more than enough for my data, and there will very likely be leftover space in the 250GB disk. Help me decide what to do with the leftover space.
[/list]

Here's the hardware, in case it matters:

```

1x Asus P5K-SE Motherboard
1x Intel Core 2 Duo E7200 Processor
1x 2GB Kingston RAM stick @ 800MHz (Yes, I know two 1GB sticks would be faster on a dual-core system, but I intend to buy a second 2GB stick when I have more money)
1x 500W PSU
1x 250GB SATA HD
1x 500GB SATA HD
1x GeForce FX8600 GPU
1x Cristal 5.1 SoundCard
1x 3.5" Floppy Drive
1x 3.5" Card Reader
1x LG CD/DVD recorder
1x Wireless Keyboard + Mouse combo set

```

Sorry for the long OP, but I wanted to provide all possibly relevant information I could without having the computer here (like I said, it arrives Friday). I also apologize for all the BSD-related questions, but since I haven't even chosen which *BSD to use, I wouldn't know where else to ask.

Thanks in advance to everyone who has the patience to read trough my post, and twice as much to anyone who replies.

Also, every tl;dr gets a rude limerick written about his/her username and/or avatar.

---

### Post by caljohnsmith on 2008-11-14
> **GepettoBR]
a)What size should the GRUB-only partition be if I want it to be big enough to house GRUB2 when the stable version finally gets released? 
[/quote]
Your dedicated Grub partition can be about as small as you can make it said:**
> 
b)What filesystem would be best for the GRUB partition, and why?

It can be any file system native to Grub, such as FAT32, ext2, ext3, etc. I've found that ext3 works well because it seems to have less file system overhead than FAT32, which is ideal for a super-dinky dedicated Grub partition. :)
> **GepettoBR]
c)Even though GRUB will work well from a primary or logical partition, would there be any advantage or disadvantage to either?*
[/quote]
Fortunately, it makes no difference to Grub whether it is on a primary or logical partition.
[QUOTE=GepettoBR]
d)Since Ubuntu will be my main OS, would there be any advantage or disadvantage in installing it to a primary partition instead of a logical partition?*
[/quote]
No advantage that I can think of said:**
> 
e)Should *BSD go to a primary partition or a logical partition?*

f)With what filesystem should I format the *BSD partition, or should I allow the *BSD installer to format it for me?

g)Will *BSD be able to share my swap partition with the Linux distros, will it require its own swap partition or does it use another virtual memory method (like Windows' paging file)?

I haven't used BSD in about 10 years, so I have no idea if it matters whether it has a primary or logical partition or whether it can share the swap partition; sorry I can't help with that one. :)
[QUOTE=GepettoBR]
h)With an initial 2GB of RAM and every intention to buy more, what is a reasonable amount of swap space for this configuration?
[/quote]
The general rule has always been swap should be 2X your RAM, but I've heard a swap larger than 4 GB is in most cases not necessary. You could even do a swap of 2 GB and most likely be just fine.
[QUOTE=GepettoBR]
i)I doubt my swap partition will be used at all (I only want one to be on the safe side) but just in case: is it better to place it on the same disk as my OSes, or on the same disk as my data?
[/quote]
I don't think it makes any difference, but probably somebody will disagree with me. 
[QUOTE=GepettoBR]
j)I have read about the possibility of a previously installed OS not being able to find the swap partition if a posterior installation formats it, but I have not found a way to solve this. If this does happen, is the fix a simple matter of editing /etc/fstab?
[/quote]
Yes, exactly; if you use a UUID to identify your swap partition in your fstab, reformatting the swap partition will most likely change the UUID, so you just have to update your fstab with the new UUID. Another file you should be aware of that uses the swap partition UUID is /etc/initramfs-tools/conf.d/resume. If you update that file, you then have to update your initrd images in the boot folder via:
```
sudo update-initramfs -u -k all
```
Anyway, that's just my 2 cents; I'm sure some other people will share their opinions too. Good luck and let us know how it goes. :)

---

### Post by Shazaam on 2008-11-14
Just a personal opinion...
The only partition I set as primary is Windows. The rest are logical inside of an extended partition sharing a single swap. Grub is on sda.

sda-SATA drive=
  sda6-PuppyLinux
  sda7-Mepis
  sda8-Ubuntu 8.04
  sda9-" " 8.10

sdb-PATA (IDE) drive
  sdb1-WinXP
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    5  Extended
/dev/sda5             126     4369679     2184777   82  Linux swap / Solaris
/dev/sda6         4369743    53817749    24724003   83  Linux
/dev/sda7        53817813   136086614    41134401   83  Linux
/dev/sda8       136086678   426798854   145356088   83  Linux
/dev/sda9       426798918   625137344    99169213   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161    7  HPFS/NTFS

```

---

### Post by GepettoBR on 2008-11-15
Thanks a lot, both of you. I didn't even know I could make a partition as small as 5MB... All I have to do to install GRUB is copy the files from (for example) my current Intrepid's /boot/grub to the dedicated partition and run 
```
root (hd0,x)
setup (hd0)
```, right? And repeat the process with newer files if I want to update it?

Shazaam: So you're saying that apart from Windows being moody, it makes no difference if a partition is logical or primary? I hadn't even thought about setting up a disk as one bi extended partition. What made you decide to do that?

Also, there was something that slipped my mind when I wrote the OP, and that is: Where should the "Bootable" flag go? On my current system (Windows/Ubuntu) GRUB resides in the Ubuntu partition (logical, ext3) but the Windows partition is set to bootable, but if I have a dedicated GRUB partition, shouldn't that be the one with the flag?

Thanks again for the quick and thorough replies!

---

### Post by caljohnsmith on 2008-11-15
> **GepettoBR said:**
> Thanks a lot, both of you. I didn't even know I could make a partition as small as 5MB... All I have to do to install GRUB is copy the files from (for example) my current Intrepid's /boot/grub to the dedicated partition and run 
```
root (hd0,x)
setup (hd0)
```, right? And repeat the process with newer files if I want to update it?

That's exactly right, you can simply copy the files over if you want and reinstall Grub to the MBR with the above commands. 
> **GepettoBR said:**
> 
Also, there was something that slipped my mind when I wrote the OP, and that is: Where should the "Bootable" flag go? On my current system (Windows/Ubuntu) GRUB resides in the Ubuntu partition (logical, ext3) but the Windows partition is set to bootable, but if I have a dedicated GRUB partition, shouldn't that be the one with the flag?

Thanks again for the quick and thorough replies!
The boot flag is for two purposes: one is that some BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable, because the BIOS assumes the drive is then a data drive with no bootable OS. The other purpose for the boot flag is for Windows type MBRs that merely boot whichever partition on the HDD is marked as bootable. But Grub can boot an OS regardless of whether the boot flag is set on the OS's partition, so if you use Grub, it is entirely arbitrary which partition you set as bootable. I would recommend though setting either a primary partition or the extended partition as bootable, and not a logical one, because for those BIOSes that require the a boot flag to be set in order to boot a drive, I think they normally just look at the partitions listed in the MBR, which would exclude the logical partitions. :)

---

### Post by TeXtonyx on 2008-11-15
I have XP as primary and bootable. With Ubuntu and OpenSuse, I put
grub into the /boot partition of each Linux system. Then capture
512 bytes of the boot sector for each Linux OS and put a *nix.bin
in the C:\ root directory. Edit boot.ini and each OS is bootable
from XP. You can put a Linux OS as the default with a short timer. 

I also make each OS bootable from the OpenSuse grub menu.lst and
the Ubuntu grub menu.lst. You definitely should have Super Grub Disk.
If any one Linux OS becomes unbootable, XP will still boot and the
other Linux OS's will still boot. If XP becomes unbootable, the
SGD will let you boot any of the other Linux OS's. They don't
depend on each other to boot. You could put Damn Small Linux on 
your second data drive with a grub menu.lst that allowed booting 
all the OS on your first drive; sort of another backup that you
could boot from by changing the bios to boot from the second drive. 
Your computer might have one of the Function keys, F8? that lets
you switch which drive you boot from without changing it in bios.

Slackware 3.5 was one of the earliest OS that had a live cd that
offered the chance to install to the hard drive. Nice community.

My idea is redundancy rather than fragility, like networks, that
carries the theme of backup, backup, backup, like location, ...*

I didn't like BSD, but I got to try Solaris when they donated 
some Solaris OS when I was taking Linux in college. 

[http://news.cnet.com/Sun-releases-Solaris-10-for-free/2100-1016_3-5559021.html](http://news.cnet.com/Sun-releases-Solaris-10-for-free/2100-1016_3-5559021.html)

So it's now free! That is my recommendation. Besides having great
forums they have even better documentation. My philosophy is to
have the best computer experience for the user possible, rather
than to be zealous for one approach or OS. If I could, I would
even have the unix Mac OS because I hear they have the best text
editor of all the systems, BBedit. I don't think of Emacs as a
text editor since you can web browse, its self-programmable and
a tight integration with TeX (Knuth and I have same birthday) so 
I think of it as closer to an OS. I wonder if BBedit works on Ubu.

I used to dual boot RedHat6 but Fedora is no longer on top.
Have a lot of fun, I mean you already are! One of those Linux
OS I think you have to compile every program from scratch.
Now isn't that a learning experience ;-)

byw, BootitNG has a boot manager that lets you have like 25
primary partitions. And the users on that forum are into having
complex and several OS installed. It might be entertaining.

---

### Post by GepettoBR on 2008-11-15
> **caljohnsmith said:**
> The boot flag is for two purposes: one is that some BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable, because the BIOS assumes the drive is then a data drive with no bootable OS. The other purpose for the boot flag is for Windows type MBRs that merely boot whichever partition on the HDD is marked as bootable. But Grub can boot an OS regardless of whether the boot flag is set on the OS's partition, so if you use Grub, it is entirely arbitrary which partition you set as bootable. I would recommend though setting either a primary partition or the extended partition as bootable, and not a logical one, because for those BIOSes that require the a boot flag to be set in order to boot a drive, I think they normally just look at the partitions listed in the MBR, which would exclude the logical partitions. :)
Okay, thanks! I'll just leave the flag in the Windows partition then (since that's where the Windows installer will put it anyways) :)

> **TeXtonyx said:**
> I have XP as primary and bootable. With Ubuntu and OpenSuse, I put
grub into the /boot partition of each Linux system. Then capture
512 bytes of the boot sector for each Linux OS and put a *nix.bin
in the C:\ root directory. Edit boot.ini and each OS is bootable
from XP. You can put a Linux OS as the default with a short timer. 

I also make each OS bootable from the OpenSuse grub menu.lst and
the Ubuntu grub menu.lst. You definitely should have Super Grub Disk.
If any one Linux OS becomes unbootable, XP will still boot and the
other Linux OS's will still boot. If XP becomes unbootable, the
SGD will let you boot any of the other Linux OS's. They don't
depend on each other to boot. You could put Damn Small Linux on 
your second data drive with a grub menu.lst that allowed booting 
all the OS on your first drive; sort of another backup that you
could boot from by changing the bios to boot from the second drive. 
Your computer might have one of the Function keys, F8? that lets
you switch which drive you boot from without changing it in bios.
So each of your bootloaders can boot every OS... Yeah, that's pretty safe. But the Windows bootloader is too much of a hassle to go through - I think I'll combine your idea with the dedicated GRUB, and just keep my GRUB CD and floppies around. Thanks!

> **TeXtonyx said:**
> Slackware 3.5 was one of the earliest OS that had a live cd that
offered the chance to install to the hard drive. Nice community.
I've always heard that Slackware is way too difficult to learn for a beginner, that nearly nothing is automated. How much trouble can I expect from it?

> **TeXtonyx said:**
> Have a lot of fun, I mean you already are! One of those Linux OS I think you have to compile every program from scratch.
Now isn't that a learning experience ;-)
That would be Gentoo, right? I'm really excited about seeing how it turns out after I'm done installing (based on what I read, I'll probably have to set aside a weekend to do it).
> **caljohnsmith said:**
> BootitNG has a boot manager that lets you have like 25
primary partitions. And the users on that forum are into having
complex and several OS installed. It might be entertaining.
I thought that the cap on 4 primary/extended partitions was an MBR limit, not a bootloader limit. How can a bootloader get past that restriction?

EDIT: Well, it's closed-source software and it's Windows-oriented so that doesn't really matter. I think I'll stick to my GPL'ed GRUB for the time being (and I'm not about to shell out $50 for it either).

---

### Post by GepettoBR on 2008-11-16
[http://docs.pcbsd.org/guide/](http://docs.pcbsd.org/guide/)
> Be aware that BSD operating systems, and hence PC-BSD, only recognise primary partitions and consider any logical partitions as a whole primary partition. Trying to install on a logical partition will convert your extended partition into a primary partition and erase all logical partitions of your system. PC-BSD can be installed on any primary partition; it doesn't necessarily have to be on the first one. Be careful and make sure you have a backup of your data.

With this and everyone's kind replies, all my questions have been answered. I'm marking this thread as solved, and when I have a running multiboot I'll post back with my grub.conf and any other relevant information. Thank you very much for the help.

---

### Post by Shazaam on 2008-11-16
If you are worried about tweaking things 'till they break, download and install some kind of virtualization program (VMware, VirtualBox, etc). Then you can set up/tweak/partition/format/trash installations to your hearts content without worrying about messing up your real (non-virtual) setup.

---

