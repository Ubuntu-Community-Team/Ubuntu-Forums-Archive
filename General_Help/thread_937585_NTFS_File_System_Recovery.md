---
title: "NTFS File System Recovery"
date: 2008-10-04
forum: General Help
---

### Post by Metallibus on 2008-10-04
First of all, I'm not sure if this is the right place for this post or not, but I did my best =X

Anyways,

I've been thinking about installing some form of Linux for a long time now, and one of my roommates just convinced me to get Ubuntu and try it out. I decided to give it a shot but now I've run into problems. I'm pretty computer "literate" but I've never used linux in my life, mostly windows and DOS. I have a fair understanding of DOS command line and know some basic stuff about the Linux terminal/command line (not sure if there's difference).

I have an Alienware laptop with two hard drives (~150gb each, running Intel Matrix Storage Manage (Software RAID), Model ST9160823AS) in RAID 0, so this caused me trouble enough getting Ubuntu to recognize them correctly (more on this later). I had Vista installed on a ~200gb partition with XP installed on a 90 gb partition (both NTFS). I decided since I don't use my XP anyway, to format it, and shrink it, and put Ubuntu on it. I wanted to keep my Vista install intact, and read this was possible (with the exception of the RAID part).

Using the Vista partition utility, I formatted the second (xp) partition, and expanded my vista partition to leave 40gb unallocated. I booted an Ubuntu 8.04 live cd and tried to install. It recognized my drives individually and couldn't read the files due to the lack of RAID support. I looked around and figured out how to add the dmraid package through the live cd, and continue with an installation. Dmraid allowed GParted to pick up on the RAID setup, and could correctly read both partitions on the drive. I continued with the install, but it refused to let me do the Automatic partitioning, and forced me to do it manually.

I couldn't find very clear directions on how to do this correctly, as most other tutorials weren't assuming RAID setups, or seemed like difficult console tinkering that felt over my head. I followed a pictorial tutorial on how to use FreeBSD to replace the GRUB boot by forcing linux to install GRUB to it's own partition instead of the entire disk, as I didn't like the idea of letting linux take over my boot sequence/record etc anyway. (can't seem to find the link again)

I made a swap partition of 3gb, and left the rest to Ubuntu, though I wasn't sure about how to format it. It seemed like most people used reiserfs, but the tutorial I was following said you must do it as ext3. I trusted the tutorial, selected ext3, and proceeded to let it install. The tutorial said to click advanced on the last page, click advanced, and change the boot record location or something to something like /dev/sdb that matched your drive location shown before. Mine showed up as something like isw_bjdfhhaagd_volume0 (stripe) so I tried interpreting these directions, but I guess either I didn't or ubuntu got lost with the RAID stuff.

So I gave it a shot and it said that there was an error writing the ext3 filesystem, and kicked me back to the partitioning step. I figured Id try doing it as reiserfs as I saw most other people say to do (including my roomate) and give up if it didn't work. I tried doing the bootloader stuff normally (I think) and it gave me another error, saying something else about not being able to write the filesystem. At this point I was ready to give up when it kicked me back to the partition step and things looked completely different. I opened up gparted and it showed the entire drive as being formatted as reiserfs.

At this point I knew I had most likely lost all my data. I rebooted without the LiveCD and got the standard "Cannot find a bootable device, insert one and press any key" error. I tried out the Vista DVD and it wouldnt recognize partitions/installs. I told it to try startup recovery and it took about 20-30 minutes and said that it had found a problem with the partition table and had attempted to repair it, and said I should attempt to reboot. I rebooted, and it still wouldnt. I gave the Vista disc another shot, and it said the same thing and still no dice.

At this point I went back to the Ubuntu LiveCD and started looking for file system recovery support online. I found some decent software, but all .exes Ubuntu couldn't open. I found a site ([http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html](http://www.faqs.org/docs/Linux-mini/Partition-Rescue.html)) with a lot of different suggestions on how to prepare incase something like this happened and what to do if it did. About 4/5 of the way down there is a large section saying GParted can attempt to recover mis-written file systems. I booted up GParted (gui version), and what do you know, it recognizes 1 of them...

GParted is now *somehow* recognizing my old 90gb XP partition that I had from before this all happened, and my old 209.17 GB where vista data WAS (and still SHOULD BE but has no file system) but it is reading it as unallocated. I don't know if this is due to my vista recovery, and maybe a few more tries would eventually recover my old install too, but my XP isn't bootable, and it used to be. Maybe the MBR is broken, but that should repairable as well.

I tried messing around with similar commands with gparted in the terminal but I get is:

ubuntu@ubuntu:/rofs/usr/bin$ /rofs/usr/bin > gpart /dev/mapper/isw_bjdfhhaagd_Volume0
bash: gpart: Read-only file system


I would be very thankful if someone could tell me if there is a way to restore the NTFS file system and possibly recover some, if not all of my data. Most of it isn't *that* important, but it would save me a lot of time if I could restore it. I think it should be possible, as the installer gave me an error after ~30 seconds, so I can't imagine it formatted that quick, so I *think* my data must still be there and be recoverable.

I'll keep looking around and try to post more relevant info when I can.

Please someone help me :(


PS: I have vista installed on an external that I *should* be able to boot off of if this helps...



PSS: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) Seems to be the type of program that could do this. I'm not really sure what to do with it, I'm poking around with it but I don't really understand it all...

I found specs saying the logical chs is 16,383/16/63 but this comes out way smaller if I enter it into testdisk it comes out way too small. How do I set this up for a raid drive? or do i just leave the default 625154560/1/1?



EDIT: Sorry for the huge wall of text....


[B][U]tl;dr version:
[/U][/B]
I attempted to install Ubuntu on a second partition (dual boot) on a RAID 0 set up, but somehow failed and corrupted/erased/replaced my NTFS File System/Partition Table. GParted is supposedly able to recover this, but I can't seem to figure out how to do it.

---

### Post by Metallibus on 2008-10-04
Still looking for help on this.

It seems to be gone, I can't find a way to recover anything.

---

### Post by aysiu on 2008-10-04
[This guide](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/) will help you get back your data.

Let us know if you get stuck on a particular step.

---

### Post by Metallibus on 2008-10-04
That guide looks like it's just doing file recovery. Is it possible to recover the filesystem and my vista install as well?

At the end he says they should be visible back in windows, but I can't check without reformating/reinstalling to my hard drives.

If I'm going to have to reinstall windows again, I'd like to install Ubuntu with it as well. I've found multiple dual boot guides and multiple RAID how tos, but I don't know enough about linux to try to combine the two. Are there any Dual boot RAID guides? Or is there an easy way to follow a dualboot guide while raided?



EDIT: Also, I'd like to backup to a 90gb external, but it's formatted in NTFS. Will photorec still be able to write to this? Also, I had about 200 gb of data, though I doubt it'll pull everything out anyway.

---

### Post by aysiu on 2008-10-04
> **Metallibus said:**
> That guide looks like it's just doing file recovery. Is it possible to recover the filesystem and my vista install as well?

At the end he says they should be visible back in windows, but I can't check without reformating/reinstalling to my hard drives.

If I'm going to have to reinstall windows again, I'd like to install Ubuntu with it as well. I've found multiple dual boot guides and multiple RAID how tos, but I don't know enough about linux to try to combine the two. Are there any Dual boot RAID guides? Or is there an easy way to follow a dualboot guide while raided?



EDIT: Also, I'd like to backup to a 90gb external, but it's formatted in NTFS. Will photorec still be able to write to this? Also, I had about 200 gb of data, though I doubt it'll pull everything out anyway.
It is just for doing data recovery, but I figure that's a first good step before trying to fix the partitions.

And, yes, *photorec* can write to an NTFS external drive as long as it's mounted by Ubuntu correctly (which it should be by default, if you're using a recent version of the live CD, one that's been released within the last year).

---

### Post by Herman on 2008-10-04
[> ]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/")[This guide]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/") will help you get back your data.:D Nice guide, aysiu, I'm adding a link it from my [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html"), I hope that's okay.
Your work certainly must be going a long way towards making Ubuntu more popular. 
I admire your writing and communication skills.
Regards, Herman :D

---

