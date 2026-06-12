---
title: "Intermittent USB keyboard: shows two present."
date: 2016-08-23
forum: Hardware
---

### Post by Bucky Ball on 2016-08-23
Hi all,

Xubuntu-core 16.04 on a custom desktop. I've posted about this pesky keyboard before some months ago to no avail but I've just uncovered a peculiarity so thought I'd reinvestigate with a new thread.

I have a Logitech mouse/keyboard combo. The keyboard is the K345 and the mouse the M275. Without warning and for no apparent reason (although it often happens when I don't touch the keyboard for 5-10 minutes, but not always) the keyboard totally dies. No response. After maybe two, maybe thirty seconds, up it comes again and back to normal. Over the past week or two the mouse has also been dying briefly. This wasn't happening previously when the problem first cropped up earlier in the year.

Anyways, looking in Mouse and Touchpad I notice an anomaly. While I only have the one USB wireless keyboard/mouse plugged in, Mouse and Touchpad shows I have two. The entries are

1. Logitech USB Receiver
2. MCE IR keyboard and mouse (dvb_usb_rtl28xxu)

lusb shows

```
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
```

... which leaves me none the wiser. I'm inclined to think it's the Logitech USB receiver as when I disable that and enable the MCE IR keyboard/mouse, the mouse stops working. When I first discovered this anomaly, both devices were enabled. Now it is just the Logitech but has made no difference to the intermittent keyboard/mouse.

I know there are a million other threads about this kind of issue as I have researched this off and on on numerous occasions for months to absolutely no effect whatsoever. Problem persists and I'd really like to get to the bottom of it. I'm trying to write a thesis and this keyboard will soon be smashed into little bits as I'm at the end of my tether.

Just to mention: when this first started happening I immediately returned the keyboard and mouse to the shop and swapped them for another set. No different so we can rule out this coming from the hardware. Just another issue with 16.04 for me at least, and I've had a good number. :|

Essentially, my questions are:

1/ Which entry is it in Mouse and Touchpad and how do I get rid of the wrong one?
2/ I have searched an not found a way to switch off USB power management entirely, if that is possible, as I figured that may have something to do with it considering this sometimes happens when I haven't touched the keys for awhile. Is there a way to switch off USB power management entirely to test if this is the issue???

Tnx in advance for any clues at all ...

---

### Post by Bucky Ball on 2016-08-23
Ding. Just realised the obvious. This was happening before I started using it again, but this entry

2. [MCE IR keyboard and mouse]("https://duckduckgo.com/?q=MCE+IR+keyboard+and+mouse+(dvb_usb_rtl28xxu)&t=hh&ia=web") (dvb_usb_rtl28xxu)

... is my DVB-T television dongle I've been using to watch the Olympics. I've plugged it into a USB3 port instead of USB2 and see if that makes any difference. Any idea why my DVB-T dongle is being seen as a USB mouse/keyboard combo??? I now have this with lsusb.

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:2832 Realtek Semiconductor Corp. RTL2832U DVB-T
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

All present and correct. I've also added this to /etc/default/grub. Yep, I'm trying anything but hadn't seen this one before. 

i8042.nomux=1 i8042.reset

It may have worked by itself but now the wireless is going off and on after a restart - not unusual as I've been having problems with that off and on too - so perhaps solve one, generate a newie. I'll see how it goes ...

---

### Post by Bucky Ball on 2016-08-30
Not solved but resolved. Bought a USB ... *wired* keyboard and, lo and behold, not a problem since and the wireless internet dongle has stopped playing up to (mostly). Go figure.

A drag because that means using a USB port for the keyboard and one for the mouse, but hey, its a desktop with a heap of USB ports so not the end of the world. The main thing is I can get on with writing the thesis without having to stare into space for an unknown amount of time (but usually just enough time for me to not quite hold the idea I was trying to write about) ...

---

