---
title: "Why does Ubuntu kill my bios?"
date: 2009-11-02
forum: Hardware
---

### Post by Chaoscollective on 2009-11-02
I am dead keen to complete the last stage of Microsofts sacking and start using a far superior OS, but I have a major problem.

I'll describe the typical scenario which has happened without fail over two versions of Ubuntu and three computers.

I run Ubuntu from the live CD or from a disk install, doesn't matter which, they both do the same thing.

Ubuntu runs fine, Firefox fires up and I can see the web.

Next I reboot to windows, and I have no internet connection, a look at the hardware list reveals no network adapter is present (The basic 10/100 lan built into the motherboard)

Next I reboot to Ubuntu, no internet connection.

Next I reboot and choose to enter the BIOS screen, lo and behold, no ethernet device is known to the BIOS.

Next I pull out all the cables get the side off and pull the link for clearing the bios, a quick look in the bios screen confirms that that Lan is back.

Now from here I can go on many years with trouble free (windows) service but the moment I use Ubuntu once and then leave it, my BIOS has been changed again and I have no LAN and must start delving into harware fixes again.

I have searched and read about many problems with Ubuntu and Lan but none of them involve the Lan port being so comprehensively disconnected that even the BIOS can't find it.

More importantly why us a LIVE CD session which promises not to change my computer re-writing my BIOS so that it requires a hardware fix, that's worse than microsoft, at least thay only corrupt the contents of the disc.

My first try at ubuntu was version 7, tried on an Athlon XP1700, an Athlon XP2400 and an Intel P4 core 2 duo, I have just tried the new version 9 hoping that this bug would not be present but it played out perfectly as before, mind you the last time it buggered the BIOS so completely that the machine would not respond to the on switch until I had cleared the BIOS.

I am by now itching to use Ubuntu and feel sure that this problem has a simple solution, but until I get past it I can't get to learn about the OS so that I know how to fix it.

Mark

---

### Post by peculiar penguin on 2009-11-02
Probably not the BIOS, I'd guess the NIC chip itself is put into into an invalid state by the Linux driver and the BIOS can't reset it properly for whatever reason. Happens when the manufacturer doesn't provide specs, drivers have to be created using reverse engineering, the author doesn't have (all existing revisions of) the hardware, etc. Had a similar problem years ago, was fixed by a kernel update at some point. I also didn't have to clear the CMOS, killing power completely (i.e. using the switch on the power supply or unplugging it from the wall) for a few seconds was enough to revive it.

As for your options, figure out the exact hardware and the module used and report/file a bug. Maybe no one has noticed the problem so far, maybe the maintainer is missing information you can provide,... who knows.
If these are desktop computers with free expansion slots, you could also just buy a couple of cheap NICs with a known good chipset in PCI card format and use those instead of the integrated ones.

---

