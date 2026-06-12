---
title: "Several upgrade issues"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by picante on 2009-05-24
Or rather, I didn't do a normal upgrade as I went straight from 8.04 to 9.04 (I started on Ubuntu with that version quite recently), which was mostly okay because I had very few files to back up anyway. However, the move has caused me a number of (mostly hardware related) teething issues.

- I can no longer use desktop effects at all.
- When I use Hydrogen, I can't hear anything, even though it looks to be working. (all the sound driver tests seem okay)
- If the computer goes to sleep and then wakes up, the webcam light comes on and won't go off.

I also had issues with my wireless card, but a friend managed to fix it. It seemed that Ubuntu misrecognised the card model. But even though the new driver works, it's not as fast as the old one (both are madwifi, just that they are for different models).

I'm afraid I'm extremely new to Ubuntu/linux, so I have little idea what I'm dealing with.

Thanks a lot.

---

### Post by The Toxic Mite on 2009-05-24
From what I read is that you can't use desktop effects.

Go to Applications > Accessories > Terminal and type in the following code:

```
lspci
```

Post the results of it when you're done.

**Advance Warning**: If your graphics card is an Intel one, it's likely to be blacklisted (i.e. it might've had problems during testing)

I forgot where the blacklist is, can someone get a link to the blacklist? I'm sure it's on the Compiz website or something

---

### Post by donato roque on 2009-05-24
I suggest that in upgrading ubuntu versions you can't skip over a version.  You said that from 8.04 Hardy Heron you went straight to 9.04 jaunty jackalope.  If you really want 9.04 then you can do a clean install to a separate partition.  Save you data first.  
Have a nice day.

---

### Post by picante on 2009-06-10
lspci reads: 

```
peter@peter-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Mmm Intel. So no fun for me then? The frustrating thing is that I had absolutely no display issues on 8.04.

Yeah when I first downloaded Ubuntu, I kept having problems downloading 8.10 so I tried 8.04 and it eventually worked. Then when 9.04 came out I downloaded that. I learned before install that you can't skip versions, but the download of the ISO file took me so long on this connection that I figured it probably wasn't worth it, as I had very few files to back up anyway.

Thanks a lot.

---

