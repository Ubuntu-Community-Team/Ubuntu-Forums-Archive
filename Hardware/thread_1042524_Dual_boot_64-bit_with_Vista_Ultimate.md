---
title: "Dual boot 64-bit with Vista Ultimate"
date: 2009-01-17
forum: Hardware
---

### Post by Sepulfly on 2009-01-17
Hi all, I recently bought a Sony Vaio-FW21M and since it comes standard with Vista home (32-bit, tho the notebook has standard 4g RAM) I am planning of turning it over to an Ubuntu-system. I downloaded the 64-bit version so I'm all set on that account. I do a lot of work in programs that are depending on the Windows-structure so I want to install Vista Ultimate with 64-bit support too. Now, since this is a notebook, the installation of a Win-OS, other than the one provided with the machine is not [is not done without any heartache...]("http://forum.notebookreview.com/showthread.php?t=292475")

My question concerns the dualboot. Am I ok just jamming the Ubuntu installation-cd in the drive, partitioning the disk to have, let's say 250Gig for Ubuntu and 100Gig for other purposes, and make the installation complete, and later installing Vista on the other partition, or should I first install Windows and later use the cd to partition and install ubuntu?

I want them both running, avoiding using programs like VMware or Wine who may cap speeds of some sort in certain applications. (plus I might want to play a game once in a while, so a Windows-installation can always come in handy :))

So I'd be pleased to hear what you guys suggest I do. I'd like it to be finished in one setting, cause I use the notebook on workrelated issues, can't afford losing controle for a couple of days because I messed up somewhere.

Many thanks.

Sepulfly.

(I searched but didn't quite found a thread that tackled my specific issues. If I have missed something, or if there is a better place to ask this question, feel free to say so/move thread.)

---

### Post by nixscripter on 2009-01-18
I would suggest doing it this way, which should be pretty close to a lot of guides:

1. Install Windows first, using the whole drive. If you can partition, I suppose you could, but that affects step 2.

2. Defragment the disk, and repartition it. Use a [gparted live cd]("http://gparted.sourceforge.net/livecd.php") for that.

3. Stick in the Ubuntu CD-ROM, install on the second partition, say yes to a boot loader (i.e. grub).

If you can find a guide which does it this way, I would suggest following it and asking your questions specifically as they arise.

P.S. **Do a backup** of whatever data you have on this computer (if you have any) before you try it.

---

