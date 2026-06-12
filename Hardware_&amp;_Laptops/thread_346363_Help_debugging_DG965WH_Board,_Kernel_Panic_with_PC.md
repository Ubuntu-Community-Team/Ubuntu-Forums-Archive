---
title: "Help debugging: DG965WH Board, Kernel Panic with PCI graphics card installed (Edgy)"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by toaste on 2007-01-25
Okay, so I have a Core 2 system built around an Intel DG965WH board.  Until Mesa 6.5.2, Intel mode setting drivers or 915resolution and some other bits fall into place, I won't be able to run my LCD at native resolution (won't do 1680x1050 at 60hz), so I snagged an nVidia PCI (not PCIe -- it's the low end MX4000) graphics card I had "just lying around."

The BIOS is fine and dandy with this card and will post and display its setup screen without problems.

Then I try to boot Edgy and get a kernel panic.

Question is, where, if anywhere, is dmesg or other debugging information logged to disk?  Has anybody else tried this and experienced the same thing?  I know it's an unusual setup, but a valid one nonetheless...

---

### Post by n_i_c_k on 2007-01-31
> **toaste said:**
>   Has anybody else tried this and experienced the same thing? 

Similar, yes.  Intel 945GNT motherboard plus ATI Stealth Radeon 9250 PCI graphics card.  The kernel panics on booting 6.06 AMD64 from the hard disk.  Likewise from an FC6 DVD, from a 6.10 CD and from a Kubuntu CD.

The PC will boot if the BIOS is set to use on-board graphics, and lspci shows the card:

```
$ lspci | grep VGA
0000:00:02.0 VGA compatible controller: Intel Corporation 945G Integrated Graphics Controller (rev 02)
0000:06:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
```

I attempted to write an xorg.conf to use the ATI card, but the PC locks up on starting the X server.

Help welcome.

---

### Post by n_i_c_k on 2007-01-31
The answer for me was here, [http://ubuntuforums.org/showthread.php?t=322463](http://ubuntuforums.org/showthread.php?t=322463)
I.e. boot with "agp=off".

---

### Post by CaptainPedro on 2007-12-21
I know this is a kinda old thread, but Im having the same problem and cant find much info.

I have an Intel 915G motherboard and a Diamond Stealth Ati Radeon 9250 PCI graphics card.

I can successfully boot using the integrated graphics on the motherboard, but I would like to get my card to work.

I was able to boot from a fedora 8 live cd using the options pci=nosort and agp=off, but it doesnt work with the ubuntu 7.10 live cd, or the ubuntu 7.10 thats installed on my HDD.

Thanks in advance for your help.

---

