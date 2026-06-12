---
title: "Atheros wireless not detected"
date: 2009-11-04
forum: Hardware
---

### Post by feicipet on 2009-11-04
Hi,

I bought a Samsung N310 laptop recently and loaded it with Karmic. My problem now is that my wifi adaptor can't be detected.

I know that the N310 comes with an Atheros wireless chip, but I can't, for the life of me, find out which specific chip model it is.

I know about the blacklist workarounds and have tried it but to no avail. I'm about to try compiling the latest madwifi drivers but before that, I found out something that's weird.

If I remember correctly, even if a device can't be detected, I should still at least be able to pick up an unknown device in /var/log/messages or dmesg. But here, I don't seem to be getting anything. 

According to [http://madwifi.org/](http://madwifi.org/), I should be able to see something along the lines of:

```
lspci | grep Ethernet
00:13.0 Ethernet controller: Unknown device 168c:0012 (rev 01)
```

But I don't see that either. 

So right now, I'm worried that somehow, my wifi device has been turned off, like a hardware switch that turns it off. Problem is, the laptop does not have a dedicated on/off switch for wireless. If I'm running Windows, there's a Fn key to turn it on but when I try that under Ubuntu, I get this in /var/log/messages:

```
Nov  4 20:49:03 shortstop kernel: [  885.098515] atkbd.c: Unknown key pressed (translated set 2, code 0x86 on isa0060/serio0).
Nov  4 20:49:03 shortstop kernel: [  885.098532] atkbd.c: Use 'setkeycodes e006 <keycode>' to make it known.
```

I'd like to confirm first whether I'm supposed to get at least an unknown device notification in dmesg or /var/log/messages output if I lack a driver for my Atheros chip. Hope that someone can help.

Thanks,
Wong

---

### Post by jmberros on 2009-12-25
Hey feicipet,

I also have a _**Samsung N310**_ with **_Ubuntu 9.10 NBR_** in a partition (I left WinXP in the other partition). I am experiencing your problem: Karmic doesn't recognize the wireless connection.

If it helps, let me tell you that your hypothesis wasn't correct. I logged back to WinXP and checked that the WiFi connection was ON (hitting the Fn key), then back to Ubuntu again, and still no luck.

I still can go back to WinXP and just use that, but I really wanted to try Ubuntu. Have you been able to solve the issue since Nov 4th ?

Thanks
jm

---

