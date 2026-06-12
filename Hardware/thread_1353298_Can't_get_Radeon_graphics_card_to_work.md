---
title: "Can't get Radeon graphics card to work"
date: 2009-12-12
forum: Hardware
---

### Post by piscosour on 2009-12-12
Hi,

I've spent a few evenings on this now and it's driving me around the bend! Perhaps someone here can help.

I've got an old Dell Dimension desktop PC with a standard VGA out for the onboard Intel graphics chipset, and a Radeon 9250 graphics card with both a VGA and DVI out. The machine is hooked up to a 24" HP monitor, which has many different inputs, and I've installed Karmic Koala. Here's the output of "lspci | grep VGA":

```

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
01:04.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

```I realise that it says 9200 Pro and not 9250, but XP identifies it as a 9250, and I think they both come under "RV280" anyway.

Anyhow, I can't get it to output anything through the Radeon card. I've tried connecting it up to both the VGA and the DVI ports, but the monitor says there's no signal unless I connect it back to the VGA for the onboard graphics. I tried [these instructions]("https://help.ubuntu.com/community/RadeonDriver"), which I think are for older versions of Ubuntu, but to no avail. I also tried these [specific instructions]("https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI") for RV280 and DVI, but I don't see any commented-out lines in the source file so I guess this has been fixed.

Any ideas? Is there something I have to do to tell it to output through the Radeon, and not the onboard? :confused: It definitely works on Windows.

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
Have you tried disabling the OB ghraphics in the BIOS?

---

### Post by piscosour on 2009-12-12
> **ST3ALTHPSYCH0 said:**
> Have you tried disabling the OB ghraphics in the BIOS?

No I hadn't, but after I tried that, the graphical installer just displayed a flashing cursor after I selected "install" (tried Ubuntu and Kubuntu, checked the media and it was OK) so I've tried downloading the alternate CDs instead, they get up to the disk partitioner stage and always just "hang" at 33% just before it formats the new partitions, waited an hour or so but there's not even any disk activity. Tried playing with some of the advanced settings, defining the partitions manually and using ext3 instead of ext4 and so forth but it was the same.

Just tried it with a Debian Squeeze CD and that seemed to install OK, but I get a kernel panic message after the grub screen :( Oh well, time to upgrade my hardware I guess!

---

