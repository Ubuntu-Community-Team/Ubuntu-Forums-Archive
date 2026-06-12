---
title: "Non-fatal(?) error with acpi_run_oshp"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by RainKap on 2007-02-27
Hi there

As a comparative newbie with Linux, I decided to get a fairly potent new box to run Ubuntu. It's a custom-built machine with:

Tyan Thunder n6650W motherboard
2 * AMD Opteron 2.0GHz CPU
4 * 1GB RAM
nVidia 8800GTS 640MB PCIe graphics card
Western Digital 150GB SATA HDD
2 * Seagate 320GB SATA HDD
2 * NEC AD-7173A DVD writers
3.5" floppy

I've partitioned the 150GB drive to install both Ubuntu 6.10 AMD64 version and Ubuntu 6.10 IA32 version for dual boot. Both installs ran happily, except that the installer didn't recognise the graphics card, and booted me into a command line interface. After some trial and error, I found the best way round was to use

sudo apt-get update 

followed by 

sudo apt-get dist-upgrade

to pull down the latest kernel version (2.6.17-11-generic)

then to run the appropriate nVidia install script to install the driver for my graphics card. The system now seems to be happy, *except* that when the system boots up (either into the AMD64 version or the IA32 version) I get the following error message:

[49.587728] acpi_run_oshp:\_SB_.PCIO.XVR2.NECB OSHP fails 0x5

I also noticed that in the Device Manager tree, there are some unknown devices:

Unknown (0x0377), vendor nVidia Corporation, on which hangs:
    Unknown (0x0193), vendor nVidia Corporation

Unknown (0x0378), vendor nVidia Corporation

Unknown (0x0378), vendor nVidia Corporation, on which hang:
    Unknown (0x0125), vendor NEC
    Unknown (0x0125), vendor NEC

Looking at the specs for the motherboard makes me pretty sure that the NEC devices are the NEC nPD720404, which supports the 2 PCI-express 100MHz slots (could this be linked to the failure to recognise the graphics card when I installed Ubuntu?).

Can anyone tell me, please, whether I can simply ignore the error message, or should I do some more digging to try to fix the error?

Thanks in advance for any help

Ian Park

---

### Post by RainKap on 2007-03-01
After opening up the box and poking about, as well as RTFM of the motherboard, I found that the NEC uPD720404 is the controller for the two PCI-X 64-bit 100/133MHz slots. The graphics card is plugged into a PCI-E 16x slot, so the fact that the PCI-X 64-bit 100/133MHz slots are (presumably) not working isn't a worry - it's just a minor niggle having the error messages!

It would still be interesting to see whether the error is resolvable...

Ian

---

### Post by gvoima on 2007-07-16
Hi, I'm in a progress of buying that same Tyan motherboard that you posted. Have you yet got the PCI-X ports to work and have you tested them?

And is all the rest of the hardware of that MoBo working? On the nvidia pages they say that there is support for Linux and Windows.

So I suppose it's 100% working?

Thanks.

---

