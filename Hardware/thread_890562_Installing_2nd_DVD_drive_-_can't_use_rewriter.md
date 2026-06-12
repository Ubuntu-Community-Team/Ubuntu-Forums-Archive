---
title: "Installing 2nd DVD drive - can't use rewriter"
date: 2008-08-15
forum: Hardware
---

### Post by Kevbert on 2008-08-15
I've recently had problems with my IDE DVD/CD Rewriter.  The CD part seems to work fine, but the DVD part will not recognize DVDs.  Below mis an excerpt from my messages.log file which could be the problem:
```
Aug 12 07:52:06 kevin-dt1b kernel: [   34.538154] scsi 5:0:0:0: CD-ROM            DVDRW    DRW-6S160P       PSG6 PQ: 0 ANSI: 5
Aug 12 07:52:06 kevin-dt1b kernel: [   34.551965] [COLOR="Lime"]Driver 'sd' needs updating - please use bus_type methods[/COLOR]
```
In the mean time I decide to get a new SATA DVD/CD Rewriter which I've fitted as a second drive (so that I can play music on the dodgy drive and use the second for writing CDs and DVDs). It's shown in the memory log:
```
Aug 15 10:33:54 kevin-dt1b kernel: [   33.620240] ata6.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
Aug 15 10:33:54 kevin-dt1b kernel: [   33.806996] ata6.00: configured for UDMA/100
Aug 15 10:33:54 kevin-dt1b kernel: [   33.807149] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
Aug 15 10:33:54 kevin-dt1b kernel: [   33.807208] ata5: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
Aug 15 10:33:54 kevin-dt1b kernel: [   33.808437] scsi 5:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
Aug 15 10:33:54 kevin-dt1b kernel: [   33.808495] ata6: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
Aug 15 10:33:54 kevin-dt1b kernel: [   33.818640] Driver 'sr' needs updating - please use bus_type methods
Aug 15 10:33:54 kevin-dt1b kernel: [   33.824674] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Aug 15 10:33:54 kevin-dt1b kernel: [   33.824729] Uniform CD-ROM driver Revision: 3.20
Aug 15 10:33:54 kevin-dt1b kernel: [   33.825063] [COLOR="Lime"]Driver 'sd' needs updating - please use bus_type methods[/COLOR]
```
How do I resolve this ?  Does this mean I need to install new firmware (and how) ?
If I try to burn to a blank CD (with the new drive) for example the blank CD is displayed on the desktop.  I right-click on the icon and select open with CD Creator.  I add a file and then select write to disk and the program asks for a CD to be put in the drive (but the drive already has a new CD in it !!!)
Any help is appreciated.

---

### Post by Kevbert on 2008-08-17
bump

---

### Post by ljonesj on 2008-08-17
u may not want to hear this but take out the bad drive as it may be interfering with the new one some how it may be a long shot thou

---

### Post by Kevbert on 2008-08-17
Thanks for the reply.  Unfortunately things have got worse.  I've re-installed Hardy Heron only to find the new DVD drive reboots the system when a DVD is inserted into the drive.  I've disconnected the old drive and still get a reboot.  It works fine in WinXP, but unfortunately I now have to re-register, by phone, the XP system as my hardware has changed (one reason I hate Microsoft software).
I've raised a [[COLOR="Red"]bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/258872") on Launchpad.

---

### Post by cariboo on 2008-08-17
I looks like you've made things worse by doing things the Windows way. I would suggest that you try:

```
sudo dpkg-reconfigure -a
```

With your defective drive completely remove from the computer. This may fix things without having to do another installation.

Jim

---

### Post by Kevbert on 2008-08-18
Thanks Jim.  Wow that's a powerful command.  Unfortunately I still get the reboot problem.  There looks like there may be one or two problems with that command as I was asked twice about what keyboard was installed (at different points during the reconfiguration).

---

