---
title: "Which mobile (laptop) graphics to get?"
date: 2008-11-09
forum: Hardware
---

### Post by softtower on 2008-11-09
I am shopping for a new laptop, and it seems there isn't a huge variety of video options. I just need to pick one with the best Linux compatibility.

The laptops I am looking at usually offer one of these:
[LIST=1]
[*]Intel X4500HD integrated
[*]NVIDIA Quadro NVS 160M
[*]ATI Mobility Radeon 3650
[/LIST]

I've been using Lenovo laptop with an older Intel X3100 integrated graphics and it was OK. Compiz was a bit lagging (especially in Forefox when scrolling pages) but I've been tolerating it.

So I ordered another laptop equipped with X4500HD and it's been **terrible**. Desktop effects is a big no-go: dropped frames, lagging scrolling, etc. KDE's meter shows me 16-22FPS. glxgears gives about 200. Even when effects are disabled, the system feels a bit slow: everything is accompanied with a few milliseconds of a delay. So this one goes back to Dell.

Which leaves me with 3 options:
[LIST]
[*]Wait for improved Intel drivers. And can they improve the speed by 400-500% (Because that's what it will take to make it not useless)? How long may it take?
[*]Get NVS160m. But people complain about nVidia drivers all the time, and as I notice nobody has ever managed to suspend/resume a laptop with this card.
[*]ATI Mobility Radeon 3650. I don't know much about this one. I used to have ATI FireGL 5250 card on my other laptop and it was a mess: slow, hot, with very, very, very buggy fglrx driver. It has been almost two years since, did fglrx get any better?
[/LIST]
Which card do you have? What do you recommend?
Thanks!

---

### Post by phidia on 2008-11-09
I don't know if it's entirely true that no one has gotten suspend/resume working with nvidia graphics-although it certainly can be trying to set up. With opensuse my 7150M nvidia card suspended and resumed most-but not all-of the time. 

There is an intel driver for the GMA 4500 card and some threads here too-I didn't have much luck just now finding those.

There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268615") on that card you might want to subscribe or follow that.

---

### Post by softtower on 2008-11-11
Anyone? Which graphics card are you running? My needs a simple: super-fast desktop effects plus suspend/resume.

---

### Post by the lush on 2008-11-11
The ATI card works very well in 8.04, but is unusable in 8.10, which is annoying as I selected my current laptop based upon the fact that it had this card and my previous experiences with it on an older laptop had been so good. If you are going to use 8.04, I strongly recommend it.

---

### Post by razy60 on 2008-11-11
my laptop is a couple of years old, It uses an intel 945gm graphics. I'm running compizfusion with the 3d cube, with the mac4lin desktop and Cairo  dock all without any problems(yet), all running quickly and smoothly.
I am using hardy 8.04.

---

### Post by softtower on 2008-11-11
Interesting... It seems that 8.10 is a dead horse since support for nearly every video card type has deteriorated: Intel is a no workie, now ATI... I don't mind sticking with 8.04 but the newest wi-fi cards from Intel (5100AGN and 5300AGN) aren't supported by 8.04

---

### Post by softtower on 2008-11-18
Allright, Thinkpad T500 with Intel X4500 is The ****: everything works out of the box: Compiz is super-smooth, wireless is rock solid, it suspends and wakes up *very* quickly, just like Macbooks/OSX - very impressive. All special keys work too, even touchpad is configured perfectly and needs no adjustments: just load up Ubuntu 8.10 and go.

Although my first attempt at installing it wasn't as good: perhaps because I was using "Kubuntu Alternative CD" or something... But the official Ubuntu/Gnome CD works great.

This has been by far the best "laptop compatibility case" for any new distro I've ever tried. If anyone is looking for a best Ubuntu/Linux laptop, I recommend Thinkpad T500 with Intel graphics.

Below is my lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

```

---

### Post by the lush on 2008-11-18
Congratulations, that's great news!

---

