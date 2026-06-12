---
title: "Using GParted to Move Unallocated Space to XP Partition"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by maporojo on 2008-12-26
I'm new to Linux and not a computer expert. I am unable to move ~1.5GB of unallocated space in sda2 (that contains Hardy Heron) to sda1 (that contains XP SP2). I freed up that space by resizing sda5.

(See the three screenshots in my album.)

It appears that the only thing I can do is to resize sda5 or sda6. I wonder whether this has anything to do with logical vs physical partition. To the best of my knowledge, what I have is a logical partition.

Tell me how to make sda1 ~28.5GB if you know how to do it. Thanks!

---

### Post by zvacet on 2008-12-26
First of all I don´t see any screenshots.It is not unallocated space if it is on partition with Ubuntu installed on it.You can shrink that partition from left to right so that fee space will be between XP and Ubuntu.Let that be unallocated space and after that just expand your windows partition.You can do it with [Gparted live Cd.]("http://gparted.sourceforge.net/")

---

### Post by bliffle on 2008-12-26
I just did that last night, for the first time, and I got it to work. But maybe my situation was different. Anyway, here's what I had to start with (too bad I didn't take snaps - but I remember it pretty well):

first partition was a 10gb XP partition
second was a 10gb linux-swap partition
third was my working ubuntu Gutsy Gibbon 20gb partition
after that was available space I'd left for futures

I wanted to add that linux-swap space to the XP (for MS Streets and trips). I figured that it would be best to add contiguous space, if available. Else I could have created a new partition  and made it a drive letter, etc., but that doesn't produce more "Program files" space for big programs.

So I figured I'd delete the linux-swap and then expand the XP, then re-allocate the linux-swap in that available space. 

But it looked scary, especially since I also had to change a partition to 'extended', also. And I didn't really want to blow either the XP or Ubuntu partitions. 

The only backup plan I had was to rebuild the whole thing on a fresh HDD, if I screwed up, and then finagle all the old stuff over to that newer bigger HDD, which would have right-size partitions.

But it all worked out, and took about an hour.

I deleted he linux-swap.

Increased size of the XP partition.

Allocated an extended partition from the available space at the end.

Allocated a linux-swap within the extended partition.

Tried to boot, but kept getting "Error 17".

So I stuck the old GRUB CD into the CD drive and booted from it. then I fixed the MBR to bootup partition 0, the XP, which is "(hda,0)".

I still couldn't bootup ubuntu, but I finally figured out that when I deleted that old linux-swap and put the space in XP that I had actually eliminated one partition so that the partition numbers changed.

GRUB gives a guy a chance to temp edit the boot partition list (somewhere in there when you're trying to boot it) when you get a "GRUB>" prompt and it says you can 'e' edit, or 'c' get a cmdline, or uparrow/downarrow to move around.

So I 'e' edited it and changed the line that had "(hda,3)" to "(hda,2)" to account for the removed partition, and it booted up ubuntu!

But then I had to do that every time I wanted to boot, so to make it permanent I brought up a ubuntu Terminal and started an edit:

sudo gedit /boot/grub/menu.lst

and then I edited every occurrence of "(hda,x)" to make sure 'x' was correct.

While I was at it, I also removed some old unused kernel boots that I never used anymore.

Good luck!

---

### Post by bliffle on 2008-12-26
Oh, before I started I googled around a little and found this helpful reference (I put the good stuff in bold partway down):


[http://en.wikibooks.org/wiki/GRUB_Installation_After_Windows_Installation](http://en.wikibooks.org/wiki/GRUB_Installation_After_Windows_Installation)

GRUB Installation After Windows Installation
From Wikibooks, the open-content textbooks collection
There are no reviewed revisions of this page, so it may not have been checked for quality.
Jump to: navigation, search

[edit] GRUB Installation

Installation of GRUB is a two step process. The first step is to install or build GRUB in a host OS environment, and for this we will use Linux. The second step is to install and configure GRUB as the boot loader for your system.

Compile GRUB Source Code

The first step is the usual: download the source archive, untar it, configure and make install. Assuming you have found a source mirror (see [www.gnu.org/software/grub/grub.html](www.gnu.org/software/grub/grub.html)) and downloaded the source distribution into a suitable working directory, continue with:

tar -xzvf grub-0.97.tar.gz
cd grub-0.97
./configure
make
make install

This should create the executables: grub, grub-install and mbchk; install support files in /usr/lib/grub/i386-pc/, and install the GNU information manual and man pages. For the second step of installation, we will first build and work with a GRUB bootable CD.

Preparing a GRUB Bootable CD

Follow the steps and build your GRUB Bootable CD

mkdir iso
mkdir p iso/boot/grub
cp /usr/lib/grub/i386pc/stage2_eltorito iso/boot/grub
mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso

[B]Install GRUB on MBR

Reboot your system with “GRUB Installation CD”, after load stage1 you find a grub shell. Run the following command to find which partition of your system, Linux is installed.

grub>find /boot/grub/stage1

Suppose your Linux Distribution is installed on your first Primary partition, then the output is

(hd0,1)

then you install the GRUB on your Hard Disk Master Boot Record (MBR). The steps are as following.

grub>root (hd0,1)
grub>setup (hd0)
grub>quit

The GRUB Install process is now complete. Reboot your system.[/B]
Retrieved from "http://en.wikibooks.org/wiki/GRUB_Installation_After_Windows_Installation"
Subjects: GRUB Installation After Windows Installation | Linux | How-tos

---

### Post by caljohnsmith on 2008-12-26
I looked at your screenshots, and you're right: the unallocated space is a part of sda2, your extended partition, which is just a container for your logical partitions. If you want to give that space to Windows on sda1, first right-click the swap partition and select "swapoff", and then you should be able to move the beginning of sda2 so that you shrink sda2 and create empty space before it. Then you can expand sda1 to use that space. How about giving it a shot again and let me know how it goes.

---

### Post by maporojo on 2008-12-26
Thank you very much, caljohnsmith and all the others. Selecting "swapoff" for the swap partition allowed me to do exactly what I set out to accomplish! (I've got so much to learn about Linux and computer systems in general.)

---

### Post by caljohnsmith on 2008-12-26
Glad to hear you got it to work and could extend your XP partition. Cheers and have fun with XP and Ubuntu. :)

---

