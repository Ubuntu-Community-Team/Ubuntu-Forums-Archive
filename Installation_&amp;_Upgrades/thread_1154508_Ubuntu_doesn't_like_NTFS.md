---
title: "Ubuntu doesn't like NTFS?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by bilijoe on 2009-05-09
I am opening a new business, and am in the unfortunate position of having to have Window$ available to run certain critical software. I decided on a kind of non-typical partitioning scheme, with WindowsXP loaded on the first (and primary) partition on my first IDE drive (I have 2 IDE and one SATA HDDs). 

Next, inside an extended partition is Ubuntu-Linux in the first logical partition, followed by a second logical partition that is my swap space (which never seems to get used as I have a goodly amount of RAM). So this fills my first IDE drive (only 40Gb). 

The next drive in line is a 150Gb IDE (when I say IDE, I really mean EIDE, I think, I'm just lazy), which I intend to be drive D: for Window$, and contain all my data, and everything else I can direct there, so as to leave the C: drive containing mostly only the OS and Installed programs. But, I want Ubunto to be able to see this drive, to mount it automatically at boot time, so I can put things like  my music and pictures there so they will be available to whichever OS I've booted. So, I formatted the entire drive as one big NTFS partition. 

The final drive in the scheme is a 250Gb SATA drive, which will be formatted in one piece, and Ubuntu will mount it as /home, thus isolating the OS from pretty much everything else. 

So, everything goes fine. I load WindowsXP (minimal install--I'll go back and add the specialized software, etc,. that I need later). Then I install Ubuntu 9.04, and again, everything seems to go fine. 

At the end of the error free install, when I tell the system to reboot, it cycles and boots right to Ubuntu--no Grub menu. The next time I boot, it goes straight to XP, no Grub menu. I looked at menu.lst, and didn't see anything that stuck out as strange, though it did look  a little different from what I am used to seeing. 

Next, I opened the Partition Manager, and found, at the end of the SATA drive (which was supposed to be one big EXT3 partition), a tiny little extended partition, containing a teeny little NTFS partition, and a teeny little Linux-Swap partition. Hmm. This is no good. 

I fumbled around a bit, to no avail, and then noticed (from the Partition Manager's display) that the EXT3 partition on the first drive, the Linux "system" partition, was filling up. OOPS! XP still booted and ran fine, so I decided I'd just reinstall Ubuntu. 

First I went in and cleaned up those two teeny tiny partitions at the end of the Linux /Home partition's drive--made it all EXT3 again, from end to end--and reinstalled Ubuntu. Looked great. Grub was back, I could boot either OS, I thought I was done--until I noticed that NEITHER OS could see the 150Gb drive that was supposed to be Window$' C: drive. 

Again with the Partition editor, I looked at the system and noticed that the little bit of data that is normally at the begining of the partition (the partition table, I'm assuming) was gone. The drive showed as empty. So I figured, no big deal, I'll just have the Partition Editor add a new partition table, and reformat the drive as NTFS--it's strictly a data partition, after all, so that seemed OK to me. 

But when I asked for a Partition table to be created, the NTFS option was greyed out. :confused: The only Window$ recognizable options I was given were FAT16 and FAT32. Not part of the plan. Windows is enough trouble. If I have to use it, I at least want to use it with its most robust file system. 

More fooling around, and soon XP would no longer boot. Ah crimeny, now I have to reinstall XP, and then refritz Grub. So, I bite the bullet, and fire up a live session of Ubuntu, in order to partition the disk the way I want it, so I can tell the Window$ installer to use the existing NTFS partition on the first HDD for the install, and leave everything else alone. 

But when the Live Session finally finished booting, and I called up the partition editor, for any partition I tried to create or modify, anywhere on any of the three HDDs, the NTFS option was greyed out. It's as if I was being told "eeeh, if NTFS is already there, we'll use it, but if you're going to create a new Windows-compatible partition, we don't do NTFS". 

What the hooey? Has Linux still not conquered the little glitches that originally plagued the early implementations of NTFS support?  (I.e., we were always told,"go ahead and read from an NTFS partition, but DON'T WRITE TO IT! Weird things can happen.")  

I'll use FAT32 if I have to, but if the NTFS support is still glitchy, I have code that will absolutely fix it (I have a bullet-proof read/write capable NTFS partition handler I wrote for the government a few years back, to use in some data searching programs, and I own the code--they only own the programs that used it) which I will gladly hand over to Ubuntu, or Linus, or whoever would be appropriate in order to get it implemented, and integrated into Linux, so Linux would handle NTFS as well as Window$ (actually this code error traps a few things that, when I wrote it, could still foul up Window$). In any case, back to the point. The point of all this rambling is this... [SIZE=2][COLOR=Red]

[SIZE=3]Is it safe to create an NTFS partition that you intend to be a permanent, full-time part of a Linux installation (and shared with XP), or, is it [still] unsafe/unstable--whatever the problem(s) have been?[/SIZE][/COLOR][/SIZE][SIZE=1][COLOR=Black] [SIZE=2]And, if it's safe, why is the NTFS selection greyed out, and how do I get around that?[/SIZE]

[SIZE=2]If anyone can shed some light on this situation, I'd greatly appreciate it.
___________________________________________________________

[SIZE=3]Also, I found a fairly serious bug in the Partition Editor in 9.04. To whom should I submit a bug report so it gets the attention it needs?

And who should I approach about the bullet-proof, battle tested, bug free code I have to handle NTFS partitions, so that it gets appropriate attention?
____________________________________________________

[COLOR=Green]I hope someone out there can enlighten me on this "can't create an NTFS partition here" issue. I'm frustrated![/COLOR][/SIZE][/SIZE][/COLOR][/SIZE]

---

### Post by zvacet on 2009-05-09
> Is it safe to create an NTFS partition that you intend to be a permanent, full-time part of a Linux installation (and shared with XP), or, is it [still] unsafe/unstable--whatever the problem(s) have been? And, if it's safe, why is the NTFS selection greyed out, and how do I get around that?

Yes,it is safe.Ubuntu c an read and write on NTFS.You can try download [Gparted live CD]("http://gparted.sourceforge.net/") and do the job with it.

---

### Post by olabandola on 2009-05-12
What is the error you found in the Partition Editor for 9.04? Since I am installing a new Ubuntu system shortly, I would like to know if I should use any other partitioning software.

---

