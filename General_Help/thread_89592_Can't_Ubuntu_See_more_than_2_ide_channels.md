---
title: "Can't Ubuntu See more than 2 ide channels?"
date: 2005-11-13
forum: General Help
---

### Post by ivanjs on 2005-11-13
This is part of a post I made earlier about trying to find the /dev/hd? of a dvd burner and hard drive on my 3rd ide channel.

No matter what I've read here and tried, Ubuntu won't see my 2nd and 3rd ide channel, although windows sees all 4 of my hard drives and both optical drives across all 3 ide channels.

Anyone know any trick to get Ubuntu to see the 2nd and 3rd ide port when Windows can see and mount them? 

Here's my system:
Board-GigaByte 8i915p
CPU: Intel Pentium 4, 3.0ghz 630j
1 gig RAM
4 hard drives, 2 optical drives


thanks.
John

---

### Post by grendel_khan on 2005-11-13
What's the relevant portion of dmesg? (View /var/log/dmesg, and scroll down to where it says "ide: something something". It should have some information about whether or not it's detecting your drives, and why.)

---

### Post by ivanjs on 2005-11-13
Oops. Read below...

---

### Post by ivanjs on 2005-11-13
[QUOTE=grendel_khan]What's the relevant portion of dmesg? (View /var/log/dmesg, and scroll down to where it says "ide: something something". It should have some information about whether or not it's detecting your drives, and why.)[/QUOTE]

Here's dmesg:

[4294672.376000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.376000] ACPI: bus type ide registered
[4294672.382000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294672.382000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294672.382000] ICH6: chipset revision 3
[4294672.382000] ICH6: not 100% native mode: will probe irqs later
[4294672.382000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294672.382000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[4294672.382000] Probing IDE interface ide0...
[4294672.646000] hda: Maxtor 6L200R0, ATA DISK drive
[4294673.054000] hdb: LITE-ON LTR-48126S, ATAPI CD/DVD-ROM drive
[4294673.106000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.106000] Probing IDE interface ide1...
[4294673.625000] Probing IDE interface ide1...
[4294674.143000] Probing IDE interface ide2...
[4294674.655000] Probing IDE interface ide3...
[4294675.167000] Probing IDE interface ide4...
[4294675.679000] Probing IDE interface ide5...
[4294676.194000] hda: max request size: 1024KiB
.[4294676.215000] hda: Host Protected Area detected.
[4294676.215000]        current capacity is 398294975 sectors (203927 MB)
[4294676.215000]        native  capacity is 398297088 sectors (203928 MB)
[4294676.237000] hda: Host Protected Area disabled.
[4294676.237000] hda: 398297088 sectors (203928 MB) w/16384KiB Cache, CHS=24792/255/63, UDMA(100)
[4294676.238000] hda: cache flushes supported
[4294676.239000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3
[4294676.292000] hdb: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
[4294676.292000] Uniform CD-ROM driver Revision: 3.20

And further IDE info:

[4294670.518000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
...
[4294672.376000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
...
[4294672.376000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.376000] ACPI: bus type ide registered
[4294672.382000] ICH6: IDE controller at PCI slot 0000:00:1f.1

Any idea from this?
John

---

### Post by grendel_khan on 2005-11-13
Can you also paste the full output of an 'lspci'? (Put it in CODE tags to keep it from being mangled by the forum, if you would.) I'm just trying to see if it's even seeing the host adapter.

---

### Post by ivanjs on 2005-11-13
[QUOTE=grendel_khan]Can you also paste the full output of an 'lspci'? (Put it in CODE tags to keep it from being mangled by the forum, if you would.) I'm just trying to see if it's even seeing the host adapter.[/QUOTE]

Here ya go. When I installed Windows XP, it wouldn't see the 2nd and 3rd channels until I installed the VIA RAID drivers. Ubuntu appears to be seeing the VIA RAID controllers according to lspci (last line):

```

0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 014f (rev a2)
0000:03:00.0 Ethernet controller: Broadcom Corporation: Unknown device 169d (rev 11)
0000:04:00.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d0)
0000:04:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:04:01.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:04:06.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)

```

---

### Post by grendel_khan on 2005-11-13
Support for the VIA VT6410 chipset isn't in the stock kernel. Here's what I could dig up, and some things you might be able to try:

VIA [released a driver](http://www.hentges.net/misc/howtos/p4p800_vt6410.html), but there's some kind of licensing issue. There's a [kernel patch](http://source.robertk.com/) to enable support (scroll all the way down); it's a really short patch, since it doesn't include support for hardware RAID or anything; it just enables the devices as standard IDE devices, which it looks like you're not getting.

Sorry I don't have better news for you. I suppose you could blame VIA or your motherboard vendor, but it seems to me like this should really be supported by the current Linux kernel. (If you look in the [lxr for 2.6.11](http://lxr.linux.no/source/drivers/ide/pci/), it's not in generic.c or via86cxxx.c. While this is the vanilla kernel source, not the Ubuntu source, it's apparently not supported by either.)

You can try to apply the patch, and drop a big report to either the [Ubuntu bugzilla](http://bugzilla.ubuntu.com/) or the [kernel.org bugzilla](http://bugzilla.kernel.org)... but wait! Aha! There already is a kernel.org [BUG #4060](http://bugzilla.kernel.org/show_bug.cgi?id=4060) on this issue! Which has been sitting there since... January. Oh dear. That strikes me as grievously dumb for such a small patch. Perhaps filing an Ubuntu bug referring to the kernel.org bug would help push it along, or at least get it applied to the Ubuntu kernel? I don't know much about how these things work. Perhaps (politely!) mailing the [maintainer](http://lxr.linux.no/source/MAINTAINERS) (he's under IDE DRIVER [GENERAL])?

I can tell you that it would definitely be helpful if you got the patch to run on your particular system. I had a bit of documentation for getting the Ubuntu-specific kernel source, patching and building a custom kernel, but I can't Google it up now. There are some steps different from what I recall from my Linux-Mandrake days; if you need help, ask and I'll see what I can find.

---

### Post by grendel_khan on 2005-11-14
A bit more information: the maintainer of the IDE subsystem saw it back in February. (See [this thread](http://groups.google.com/group/linux.kernel/browse_frm/thread/d03eb39a8dd2f9f8/2a051c072cb445aa?tvc=1&q=vt6410#2a051c072cb445aa) on the kernel mailing list, and [this LWN post about an update to ide-dev-2.6](http://lwn.net/Articles/123224/).) However, it hasn't been added.

More recently, there's been some [ongoing discussion](http://groups.google.com/group/linux.kernel/browse_frm/thread/cec29aaa2d342e1a/75bd024fb59718fd?tvc=1&q=vt6410#75bd024fb59718fd), revolving around gentoo having had support for the last six months, while the mainline kernel hasn't integrated the patch, which has been available for nearly a year now. I suppose one could definitely file a bug with the Ubuntu team, since that seems to be how the Gentoo team did it.

If you have questions about how to file a bug, I can help you with that, too.

---

### Post by grendel_khan on 2005-11-22
I've been following this issue, and the patch just made it in.

[Here's the commit](http://www.kernel.org/git/gitweb.cgi?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=4f1d774aadfc5a6ed1545dca180f66ab6d0f543d). It is included in vanilla kernel 2.6.15-rc2, released two days ago. Given that the [current version](http://packages.ubuntu.com/breezy/base/linux) is 2.6.12, which was released [five months ago](http://www.kernel.org/git/gitweb.cgi?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=9ee1c939d1cb936b1f98e8d81aeffab57bae46ab). I suppose it'll be a while before it percolates down to the distributions, but at least it's in the vanilla tree.

---

### Post by ivanjs on 2005-11-22
[QUOTE=grendel_khan]I've been following this issue, and the patch just made it in.[/QUOTE]

Thanks for continuing to look into this. Appreciate it. Something has suddenly happened to my windows xp install, and it now takes 5+ minutes to boot up (used to take about 45+ seconds), so using Ubuntu is looking better all the time, lol!
John

---

### Post by Izte on 2005-12-07
Has anyone tried to patch their kernel? I've got the 2.6.12-source, and the VIA610.2611rc4.patch, but I really dont know how to get this working, I'm really not good with that kind of development :)

---

