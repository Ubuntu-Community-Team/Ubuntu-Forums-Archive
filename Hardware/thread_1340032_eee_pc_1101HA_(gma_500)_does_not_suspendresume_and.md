---
title: "eee pc 1101HA (gma 500) does not suspend/resume and HAD strange audio problems"
date: 2009-11-28
forum: Hardware
---

### Post by neoscopio on 2009-11-28
I've recently adquired a eeepc 1101HA and installed Karmic on in (after filming me refuse the EULA, let's see how Asus deals with the Win OEM refunds). Out of the box, the ethernet and video card aren't working and the wireless card refuses to connect to some networks (the 1000H I had before connects to anything without a hitch). So:

Wireless: connects to some networks (works at home, fails at work, for instance) and is constantly droping and reconnecting the line when it works (signal drops to 1Mbps and resumes later to 54Mbps - it's a 802.11g network). I can kinda live with it and have read posts about the card being crappy hw. I think the drops in connection may be due to some TKIP renegotiation issues, not sure. Used to see the same stuff happen a long time ago with 801.11b with ndiswrapper on a TTLS network.

Wired: official driver site is down ever since I tried to install it. Will update when I can access the drivers.

Video: THIS is the problem and a weird one at that. Updated the system, everything (except these issues) working. Followed
[http://swiss.ubuntuforums.org/showthread.php?t=1253406](http://swiss.ubuntuforums.org/showthread.php?t=1253406)
this thread. Got both 2d and 3d working, but no sound. Actually, on rare ocasions, I had sound, but couldn't reproduce the conditions. dmesg was clean. lspci was and still is weird, it showed SCH Poulsbo next to practically every piece of hw listed, as bellow.


```

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

```

Got audio working, amazingly, by changing the line
```

Option "AccelMethod" "EXA"

```
to
```

Option "AccelMethod" "UXA"

```

But now I have no suspend to ram or hibernate, and those are really handy on a netbook. Have tried a couple of things but to no avail. Any ideas? I could really use some help...

Thanks.

---

### Post by [S|G] on 2009-11-28
Hi there!

I got an Asus 1101ha yesterday and have been fighting to get everything working ever since. I installed Ubuntu 9.10 netbook remix and surprisingly my wireless and wired networks have worked out of the box. GMA500, as expected, didn't, and I installed it using the new method described [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo"). Suspend/resume and hibernation also works.

Audio output also works fine, but I haven't been able to record anything. Have you been able to fix that?

EDIT: As for the wireless I've been experiencing intermittent signal losses as well, but I don't think its (only) hardware-related. Wireless works flawlessly on Windows, so I think its likely to be a linux driver issue.

---

### Post by neoscopio on 2009-11-28
I think yours is the first case I've seen of the wired card working out of the box. The wireless driver issue... it really looks like a problem when reseting the wpa key. I've seen something similar a couple of years ago and it was a firmware issue, so it can be either, really. The poor signal, however, is just the card being crappy. The 1000ha had a much wider range. I'm, right now, about 4m away from the router, no wall between the laptop and the router and the graphical indicator has only 2 out of 4 bars lit, indicating average/poor reception. Apparently this card should have 2 antennas and has only one. Still, intermittent wireless is better than no wireless at all.

About the graphics, I did almost that, if you look at the link I sent. Only diff is, I got the links from a post and not from the ppa. Still, it's a fresh install, so I might just install from scratch. Can you also post your lspci output here? I find the "Poulsbo" in each line to be strange enough to confirm if it's common or not.

Obrigado daqui de Portugal, já agora :D

---

### Post by neoscopio on 2009-11-30
Correcting some info. Wired card does indeed work out of the box. Don't know why it didn't work the first time I tried it, willing to just attribute it to a crappy network cable or something.

About the sound issue, kernel goes boom with the fabled "hda-intel: spurious response 0x0:0x0" error. Thought it was something that was already fixed. Still, it generally takes a while to break, and when it does, I can always reboot. Guess linux is finally ready for the desktop. It can now replicate the windows universal solution, when something breaks, reboot :P

Hibernate and suspend are still out. Any ideas?

---

### Post by nekr0z on 2010-02-08
Has anyone figured out the sound thing? Looks like I have everything working on this 1101HA except for hibernation, and hibernation works just fine except for no sound after wakeup.

---

### Post by keberjan on 2010-02-26
Ethernet cable:
For me it works out of the box.

Audio:
Output works fine. I didn't tried input yet.

Video GMA 500:
I followed these 2 tutorials and it works
[URL="http://swiss.ubuntuforums.org/showthread.php?t=1253406"]
http://swiss.ubuntuforums.org/showthread.php?t=1253406[/URL]
[http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/](http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/)

Wireless:
It's true wireless is loosing signal.

I fixed it using this command in terminal
```

sudo apt-get install linux-backports-modules-karmic

```Then restart and it should work.

I did all this yesterday on Ubuntu Netbook Remix 9.10

---

