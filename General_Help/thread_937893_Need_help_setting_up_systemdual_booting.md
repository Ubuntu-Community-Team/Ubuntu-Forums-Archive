---
title: "Need help setting up system/dual booting"
date: 2008-10-04
forum: General Help
---

### Post by Oplix on 2008-10-04
So I'm trying to set up my computer to dual boot XP and Linux.

My reason for doing this is that Linux simply isn't compatible with all of my devices, and there's Windows software which I need that can't be worked around or replaced because that would require relearning a new program, and I don't have the time to invest in that freely yet.

What I need to have:

- I need to be able to boot with either Linux or Windows (simple enough)
- I need to be able to easily move files from the Linux partition over to the Windows partition and vice-versa
- Ideally, I'd like to be able to access and run the programs from both OS's at the same time, if this is doable.
- The faster I can switch from 1 OS to the other, the better.

The Windows partition I plan to mainly use for running software and managing my mp3 player and a few other devices Linux has problems with. Since I will be doing work on the Windows partition, it's important that this runs stable (as stable as Windows can get). 

What I have set up so far:

- Linux is installed
- Windows is installed
- The computer is currently dual booting with GRUB

So I'm thinking Loadlin might be my best course for achieving this? Can somebody think of a better way for me to accomplish this?

If I do go with Loadlin, how do I stop booting with GRUB and start booting with DOS? My reason for wanting to remove GRUB is that I don't know what my devices or software are going to change, and I usually install lots of new stuff on the machine frequently, so I'd like to avoid as many complications as possible.

I've seen plenty of tutorials on how to dual boot a computer, I just want to make sure I'm not wasting my time setting up the wrong things, and I want to make sure I get it set up properly.

I may need some further assistance with loadlin or whichever method I decide to use, just to clarify the tutorials which are already out there, and to make sure I've done it correctly. Thanks!

---

### Post by phorim on 2008-10-04
I like to do drive-by loading of Ubuntu when I have access to Windows machines :-D.  

Generally I don't need to share the files between the systems. If I were to do so, I would resize my partitions and add a FAT32 partition that both OSes can play with easily.

Someone correct me if I'm wrong, but NTFS write support for Linux is a bit shakey still, and ext3 support for Windows is about the same, but they both deal great with FAT32.

As far as using Loadlin goes, I can't imagine what hardware change (except the addition of a new boot drive) would screw up GRUB.  

I've read that Ubuntu can install *inside* Windows as well, though I've not tried this.

Hopefully something I've said here helps.

---

### Post by howefield on 2008-10-04
The only way I know of to satisfy ALL of your "needs" would be to virtualise one operating system via something like Virtualbox.

Eg, Run Ubuntu as host system and xp as a guest, this will mean you are running both systems simultaneously. You need a reasonable amount of host resources, eg memory as it would be shared between the host and guest system. 

Should be ok to manage your mp3 player with, but as you don't define the other devices you need to use on windows, that might be where you have a problem.

But it is worth considering.

---

### Post by Oplix on 2008-10-05
Well, I plug virtually everything into this machine. I come by a lot of gadgets, etc that people want me to fill with this or install with that, etc. Just a bit of a hobby I guess. My main concerns are what I'll have the freedom to use rather than what I need at the moment.

However, I just discovered that my PC actually has a wireless card inside it that I never installed software for. So now I'm thinking of turning this into a network of 3 computers, 2 with Mac, 1 with Windows/Linux.

I've spent the entire day screwing around with hard drives, and setting up this and that, got lots of ideas for what I could do with the system. How does Linux handle networking computers in the hands of someone with very little experience? Biting off more than I can chew there? I'm looking for some projects me thinks.

Anyways, my plans for getting the dual boot going today were screwed over when I discovered that I'd lost my XP product key... Oh well.

BTW, I should probably mention that the MP3 is a Zune which doesn't seem to like software very much, as is. One of the reasons why I need the Windows partition to be stable. How well would the registry editing trick work to make the zune into an external drive if I was doing it on a virtual machine (never set one up to be honest).

All power to the Linux team working on that product (there is one, right? I heard correct?)0.o

I'll keep you updated if I need help once I get windows installed and can get things going again (Tomorrow HOPEFULLY).

---

