---
title: "lost sdcard reader after upgrade to 11.04"
date: 2011-04-29
forum: Hardware
---

### Post by timekillerj on 2011-04-29
Toshiba Qosmio x505-q896. Just upgraded to 11.04 and now my sdcard reader doesn't work.

In 10.10 I have to create a modprobe conf file to make it work. The file needed this line: 
```

options sdhci debug_quirks=0x40

```

I have tried with and without that line. The only useful bit in dmesg is:

```

[  278.809303] sdhci: Secure Digital Host Controller Interface driver
[  278.809309] sdhci: Copyright(c) Pierre Ossman
[  280.613219] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  280.834738] CE: hpet increased min_delta_ns to 67879 nsec
[  287.777860] sdhci-pci 0000:07:00.1: SDHCI controller found [1217:8120] (rev 1)
[  287.777881] sdhci-pci 0000:07:00.1: PCI->APIC IRQ transform: INT C -> IRQ 17
[  287.777925] sdhci-pci 0000:07:00.1: setting latency timer to 64
[  287.777938] mmc0: no vmmc regulator found
[  287.777982] Registered led device: mmc0::
[  287.778032] mmc0: SDHCI controller on PCI [0000:07:00.1] using ADMA

```

It LOOKS like the system sees the reader, but the "mmc0: no vmmc regulator found" may have something to do with it. Google was not much help.

Anyone got a clue on this ?

---

### Post by mbrekk@gmail.com on 2011-05-09
I have the same problem on my Acer Aspire 8943G.  Got the same line "mmc0: no vmmc regulator found" in dmesg when booting with kernel 2.6.38-8-generic. Have the same blacklist option as and works fine with kernel 2.6.35-28 without the "mmc0: no vmmc regulator found" line. Otherwise the lines listing mmc or sdhci in dmesg is the same with the two kernels.

[    1.655722] sdhci: Secure Digital Host Controller Interface driver
[    1.655725] sdhci: Copyright(c) Pierre Ossman
[    1.661029] sdhci-pci 0000:08:00.1: SDHCI controller found [1217:8120] (rev 1)
[    1.661065] sdhci-pci 0000:08:00.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.661112] sdhci-pci 0000:08:00.1: setting latency timer to 64
[    1.661137] mmc0: no vmmc regulator found
[    1.661178] Registered led device: mmc0::
[    1.661237] mmc0: SDHCI controller on PCI [0000:08:00.1] using DMA
[    2.801567] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

---

### Post by mbrekk@gmail.com on 2011-05-09
Tried to load sdhci and sdhci-pci without the "options sdhci debug_quirks=0x40" in blacklist. It seems like the 2.6.38-8 kernel handles this OK. I don't got the same error as with earlier kernels, BUT still no SD found.

I also tried to reload the sdhci and sdhci-pci modules with the SD card in the reader. 
sudo rmmod sdhci-pci
sudo rmmod sdhci
sudo modprobe sdhci
sudo modprobe sdhci-pci

Then I got the following messages a lot of times.

[ 2021.983611] mmc0: Timeout waiting for hardware interrupt.
[ 2021.983617] sdhci: =========== REGISTER DUMP (mmc0)===========
[ 2021.983628] sdhci: Sys addr: 0x00000000 | Version:  0x0000c401
[ 2021.983637] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[ 2021.983645] sdhci: Argument: 0x000001aa | Trn mode: 0x00000000
[ 2021.983654] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000001
[ 2021.983662] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[ 2021.983670] sdhci: Wake-up:  0x00000000 | Clock:    0x00008007
[ 2021.983678] sdhci: Timeout:  0x00000000 | Int stat: 0x00000001
[ 2021.983687] sdhci: Int enab: 0x00ff00c3 | Sig enab: 0x00ff00c3
[ 2021.983695] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[ 2021.983703] sdhci: Caps:     0x01fe32b2 | Caps_1:   0x00000000
[ 2021.983711] sdhci: Cmd:      0x0000081a | Max curr: 0x00000064
[ 2021.983720] sdhci: ADMA Err: 0x00000000 | ADMA Ptr: 0x00000000
[ 2021.983722] sdhci: ===========================================


The information isn't helpful for you, but someone else may get idea[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by HalfEmptyHero on 2011-05-27
I have the same issue. Anyone?

---

### Post by j.c.rush on 2011-05-27
Me too

Toshiba X505-Q875
Ubuntu Natty 11.04 (64-bit)

---

### Post by sectshun8 on 2011-05-28
Have you tried seeing if it recognizes an SD card inserted before you boot the machine?  It works for me :)

---

### Post by mbrekk@gmail.com on 2011-05-28
If I insert the card before booting I get the same error as listed in this tread comment #3. The errors appears each 10 sec in dmesg.

---

### Post by HalfEmptyHero on 2011-06-16
Bump. Has anyone submitted a bug for this?

---

### Post by AmanicA on 2011-06-17
> **HalfEmptyHero said:**
> Bump. Has anyone submitted a bug for this?

Probably not, will you do the honours?
I found a sort of workaround though: when I need to access a SD card, I boot of my old maverick kernel, then it works.

---

### Post by HalfEmptyHero on 2011-06-17
Heres the link to the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798995)

---

### Post by AmanicA on 2011-06-21
> **HalfEmptyHero said:**
> Heres the link to the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798995)
thanks!

---

### Post by Whorfin on 2011-09-06
Removing "firewire_ohci" from the kernel allows the sd card to work.

sudo modprobe -r firewire_ohci

I guess this is technically a workaround, but given I never use the 1394 firewire port....I can live with it

---

### Post by mortenbrekk on 2011-09-11
sudo modprobe -r firewire_ohci 
worked for me as well.:D

From dmesg with the SD-card installed:
[  147.758150] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 3627.761885] firewire_ohci 0000:08:00.0: PCI INT B disabled
[ 3627.761889] firewire_ohci: Removed fw-ohci device.
[ 3628.099089] mmc0: new SD card at address e0c7
[ 3628.138013] mmcblk0: mmc0:e0c7 SD02G 1.89 GiB 
[ 3628.139184]  mmcblk0: p1

and the SD-card was mounted in less than 1 sec.

---

