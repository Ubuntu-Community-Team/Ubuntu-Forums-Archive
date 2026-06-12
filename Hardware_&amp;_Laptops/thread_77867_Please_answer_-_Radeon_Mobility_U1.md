---
title: "Please answer - Radeon Mobility U1"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by Panthios on 2005-10-17
Hi.

I just need confirmation.
Is it true that there is absolutely NO way to get a ATI driver for this laptop graphiccard?

lspci gives:
```

0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
0000:00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02)
0000:00:0d.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0d.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:0e.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
0000:02:00.0 Ethernet controller: Abocom Systems Inc RTL8139 [FE2000VX] CardBus Fast Ethernet Attached Port Adapter (rev 10)

```

Is this graphicchip unsupported in Linux still?
I only get around 180 fps i glxgears.
Earth3d is sooooo slow. I don't expect my laptop to play the newest games in the highest details, but jeez, the CPU does all the work.

Anyone?
Just so I know if I have to sell my laptop and buy another with a better supportet gfxchip.

---

### Post by Joe_lurker on 2005-10-17
I don't know if the card is specifically supported but try and change the driver to "radeon" in /etc/X11/xocg.conf.  You will find it in the device section.

Joe

---

### Post by simohell on 2005-10-17
Radeon Mobility U1 is supported (for most parts) in the default ATI-driver you get if you do a clean install of Breezy, but not with ATI-fglxr -drivers.

I've googled for Radeon Mobility U1 driver setup for a few days now. I think the best results I've seen were something like 300 FPS, but that was with quite a lot of hacking.

For me DRI was enabled at clean install without any configuring and 180 FPS is good enough for my purposes. (a lot better than 135 + no DRI that I got with Hoary)

But if you want better 3D I'd say: buy a computer, maybe one that has a video card that doesn't share the system RAM.

What I'm quite disappointed with Radeon Mobility U1 and Ubuntu's ATI driver is that apparently MergedFB is not supported with this card. With WindosXP I could easily get extended desktop with just a few clicks.

---

### Post by simohell on 2005-10-18
Here is one link for you:

[http://weblog.zoup.org/index.php?op=ViewArticle&articleId=12&blogId=1](http://weblog.zoup.org/index.php?op=ViewArticle&articleId=12&blogId=1)

The guy didn't mention any FPS, and I haven't tried myself. (as I said earlier, what I would need is dual monitor with single desktop).

---

