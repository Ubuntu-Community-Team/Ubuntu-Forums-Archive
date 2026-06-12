---
title: "Kernel upgrade needed after hardware upgrade"
date: 2010-03-09
forum: Hardware
---

### Post by DuronForever on 2010-03-09
Hi,

Due to hardware failure, I was forced recently to upgrade the guts of my Ubuntu 8.04 LTS, not up to date, (home) server. It's gone from an Nforce2/MCP-T, Athlon XP 2500+ Barton to a G31 Asus P5KPL-AM motherboard with a Pentium D E6500 on it.

Not a bad thing in itself. After much fiddling, I got the raid sets back in order (there was a disk failure and a hardware failure near simultaneous.. ouch) and the system is now booting again, however.. it does not recognise the (onboard, gigabit) network card.

The 9.10 CDs I have recognise the network card no issue. 

So my first thought was to simply add a secondary network card, so I could get to apt and upgrade to the latest, and then go from there. I've tried 3 different RTL8139 cards plus a Winbond PCI 10Mb card. I also tried both PCI slots. The 8139s simply don't show up at all, and the Winbond came in as eth0, but wasn't usable -- it would stay down on boot, and it would not be possible to force it up. I also tried, as a long shot, a USB network card I had lying around, but while that was noticed during boot it didn't come up either. I've also tried disabling the onboard network controller. 

The 8.04.4 LTS CD I have doesn't recognise either the network card or the secondary network cards. Clearly I will need to upgrade the current system, but not having a network card makes this a lot harder than it ought to be.

What is the best solution? I suppose I could try to go through 8.04.4, 8.10, 9.04 and 9.10 using the alternate install CDs as non-network upgrades, each time checking when I can stop using the inelegant one, but that seems errorprone at best.

The other option, I suppose, is simply to get a much older motherboard. I could exchange motherboards with my current desktop and presumably that would work, but it would be one pig of a job. Any other suggestions? Perhaps an (inexpensive) USB or other network card that would work to  get me back up and running?

---

### Post by adam814 on 2010-03-09
That surprises me a little.  Every time I've had to install/replace a wired NIC I've just bought the cheapest one I could find at a retail store.  They've usually said they're supported by every Windows version from 2000 on (which is usually a hint it will work fine in Linux).

Of course you could also get a wireless NIC for it.  You might have to do some looking around to see which ones you could use out of the box with Hardy though.

I'd only try it as a last resort (DEFINITELY back up anything important first), but you could swap the HDD with your older desktop and try to update it using hardware that (hopefully) Hardy supports.

---

### Post by DuronForever on 2010-03-10
Yeah, I haven't had this issue with network cards before either (at least, not in this decade, or the previous for that matter -- the 90s might be different)

By now I've tried the upgradepath using a whole stack of alternate install CDs (which was a pain, but not as much as most of the other things I can think of -- and I did this on dd-generated clone disks, rather than the originals, just in case), and I can confirm that with CD kernels, at least, the onboard network card magically starts working after going 9.04 -> 9.10, and we're talking about (now ssh works, easily pastable.. :P):

01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

The PCI-based RTL8139 still doesn't show up properly (or at all in ifconfig -a), although the onboard did end up being eth1, eth0 presumably being reserved for the realtek, but this is now no longer a big deal.

However, if that means that the pci bridge chip is an Issue, then I'm in trouble -- I still have a PCI-based SATA card to reinstall, which handles the storage part of this (home) server. That, however, is currently taking a massive backseat to the very satisfactory fact that mail is once again coming in :)

---

### Post by adam814 on 2010-03-10
[https://lists.ubuntu.com/archives/kernel-team/2009-March/004797.html](https://lists.ubuntu.com/archives/kernel-team/2009-March/004797.html)

Apparently this did get fixed in later versions of linux-ubuntu-modules in Hardy.  I'm guessing your PCI bridge chip is probably OK since that particular Realtek card has issues in Hardy as well:

[https://bugs.launchpad.net/ubuntu/+bug/215450](https://bugs.launchpad.net/ubuntu/+bug/215450)

---

### Post by DuronForever on 2010-03-10
Well, at the moment it's running 9.10 with a full dist-upgrade as of yesterday, and still not recognising the 8139. That's gotta be something different than that bug. I will have to do more testing (primarily, trying the SATA card) for the next step, but this will not be today. Tomorrow is my day off, so I'll have some time then.

[Edited to add:] Right, tried that and the SATA card works without issues (although mdadm found it necessary to assemble my drives as a 3-out-of-4 plus a single orphan md -- blegh. 10 bleeding hours it takes, to rebuild a 1T drive). Still odd.

---

