---
title: "nvidia mcp55 ethernet not working"
date: 2008-05-31
forum: Hardware
---

### Post by mvnt on 2008-05-31
My motherboard is a p5n32 sli-premium, with dual nvidia mcp55 ethernet device. No problems with either Edgy, Feisty or Gutsy. But when I installed Hardy, I had no internet.
 I've tried selecting DHCP instead of roaming, or configuring it manually. None of that worked, as everything is set to "0.0.0.0" (IP, etc). Someone has any ideas/suggestions? I'll glad to provide any information requested.

---

### Post by dabang on 2008-05-31
I have a Gigabyte GA-M55S-S3 with MCP55 network device:
```
# lspci | grep -i ether
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
```
Works fine. Configured via dhcp durig installation of Gutsy. Sorry, no clue why it doesn't work on your installation of Gutsy... :confused:

---

### Post by mvnt on 2008-05-31
I'll make it more specific.

Motherboard: P5N32-SLI Premium/WiFi-AP
Chipset: NVIDIA nForce 590 SLI MCP
LAN: NVIDIA nForce® 590 SLI&#8482; built-in dual  Gigabit/ MAC with external Marvell PHY   Support NVIDIA DualNet® technology

No problems with either Edgy, Feisty or Gutsy. But there is with Hardy. The problem also exists in Debian 4.0 etch. Fedora 9 is OK.

The problem:
I don't have internet, it doesn't communicate with the modem router to get ip.
I also don't have lan, I cannot connect to my other computer through a switch.

So what I think is that something is wrong with either dhcp, network manager in gnome or the driver(although forcedeth is loaded).

It finds that I have ethernet device and what model but cannot communicate through it.

It's a very serious problem, at least to me, and if someone can help please do it.

---

### Post by JJoel on 2008-08-22
I've got the same problem.
I'm using a Gigabit ga-m61pm-s2 with ubuntu 64bit. (Also tested with 32bit).

Forcedeth is loaded and still no netwoking, The card will not turn on.

The system recognises it exist but will not turn on.

I believe it is a driver issue.

---

### Post by kayosiii on 2009-05-25
[http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427](http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427)

---

