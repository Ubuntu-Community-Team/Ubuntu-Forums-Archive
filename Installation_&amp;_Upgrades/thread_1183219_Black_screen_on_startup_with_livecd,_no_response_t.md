---
title: "Black screen on startup with livecd, no response to input."
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by Centx on 2009-06-09
I tried booting the live-cd with ubuntu 9.04, and now fedora 11, but all I get when the Desktop is supposed to appear is a black screen with some colored lines, and nothing happens when I try to change to VT with ctrl+alt+f1 or move the mouse. Any tips? should I file a bug or something?

One hw might be a bit special, a radeon HD 3850 AGP, Sapphire I belive. I think this originally is supposed to be PCI-express, but uses some adapters or something.

thanks for reading =)

Also some diagnostics from my current working 8.10-install:
```
terminal-# lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1c.0 PCI bridge: Intel Corporation 6300ESB 64-bit PCI-X Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 6300ESB USB Universal Host Controller (rev 02)
00:1d.1 USB Controller: Intel Corporation 6300ESB USB Universal Host Controller (rev 02)
00:1d.4 System peripheral: Intel Corporation 6300ESB Watchdog Timer (rev 02)
00:1d.5 PIC: Intel Corporation 6300ESB I/O Advanced Programmable Interrupt Controller (rev 02)
00:1d.7 USB Controller: Intel Corporation 6300ESB USB2 Enhanced Host Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 0a)
00:1f.0 ISA bridge: Intel Corporation 6300ESB LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 6300ESB SATA Storage Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 6300ESB SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 6300ESB AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV670PRO [Radeon HD 3850]
02:01.0 Ethernet controller: Intel Corporation 82547GI Gigabit Ethernet Controller
04:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:04.0 RAID bus controller: Promise Technology, Inc. PDC20319 (FastTrak S150 TX4) (rev 02)
04:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```
```

```

---

### Post by wpshooter on 2009-06-09
Have you tried the safe grahpics mode parameter ?

---

### Post by Centx on 2009-06-09
> **wpshooter said:**
> Have you tried the safe grahpics mode parameter ?

In fedora I found no such parameter when booting, for 9.04, I tried, but with the same result.

---

### Post by wpshooter on 2009-06-09
> **Centx said:**
> In fedora I found no such parameter when booting, for 9.04, I tried, but with the same result.

Don't know anything about Fedora, but on Ubuntu, download, burn and install from the ALTERNATE (text based) CD version instead of live version.

---

### Post by Centx on 2009-06-09
> **wpshooter said:**
> Don't know anything about Fedora, but on Ubuntu, download, burn and install from the ALTERNATE (text based) CD version instead of live version.

Thats the problem. 8.10 works ok, but without the live-cd I can't know if 9.04 will work. And installing it without borking my original partition setup means installing over my working (and customized) 8.10 installation, which I don't want to before I know if 9.04 will work.

I guess I could try with some spare disk or something, if I can find one, but shouldn't the 9.04 work when 8.10 worked?

---

### Post by wpshooter on 2009-06-10
> **Centx said:**
>  if I can find one, but shouldn't the 9.04 work when 8.10 worked?


If you have used Ubuntu very long, you will know that that logic does not necessarily hold true, unfortunately !!!

---

### Post by Centx on 2009-06-10
> **wpshooter said:**
> If you have used Ubuntu very long, you will know that that logic does not necessarily hold true, unfortunately !!!

Yeah, too bad really. I'm wondering if I should  submit it as a bug though.

---

### Post by ronparent on 2009-06-10
The strongest possibilities for 9.04 not booting are 1) bad cd 2) apic,lapic incompatibility. If it is a newer mb especial the 2nd is likely (also the easiest to check). On the first boot screen (after selecting language) hit F6 for options, and, select noapic, nolapic. If we get lucky that will fix the problem. Other wise you would have to check the mdsum on the cd.

---

### Post by Centx on 2009-06-10
> **ronparent said:**
> The strongest possibilities for 9.04 not booting are 1) bad cd 2) apic,lapic incompatibility. If it is a newer mb especial the 2nd is likely (also the easiest to check). On the first boot screen (after selecting language) hit F6 for options, and, select noapic, nolapic. If we get lucky that will fix the problem. Other wise you would have to check the mdsum on the cd.

Was a bad cd actually, probably burned it too high speed. And this was with my new cd-burner =).

Well, I got it to work. Seems like the default driver for my gfx-card (I assume "ati") doesn't work, so changing to "vesa" made live-mode usable. So I installed fglrx to test in live-mode, and it worked.

I have now installed 9.04, and it seems to be much like 8.10 to me. ext4 as root partition, and most all things works out of the box. Even ET:QW works, although I've got major performance problems.

Should I file a bug for this? (AFAIK this should be a bug with the ATI-driver, or radeonhd, if that's the default one).

---

