---
title: "ATI/Intel hybrid issues + Wine"
date: 2010-12-23
forum: Hardware
---

### Post by temnix on 2010-12-23
I've already posted this on WineHQ forums, no replies there. So here's hoping.

I just bought a new laptop and decided to go for Linux. I'm getting to know the Terminal slowly, but I'd like to run Oblivion and Fallout 3. The specs are sufficient. The problem with these games (I haven't tried others with Wine yet) is that they don't seem to recognize the other graphics card in there, in addition to the Intel chipset, and that is Radeon HD 5700. In fact I'm not sure Ubuntu knows about it at all, and it's hard to check when you can't run the games!

Here is what I know:

```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]
```Seems to be here, but under Wine the Options of Fallout and Oblivion show the Intel chipset as the graphics card in use. Which may be true, I don't know a way to see which card is active or switch to it. There was a program I downloaded, gone now, that let me force-switch to the Radeon, but then Options of Oblivion detected NVidia 7900 instead!

How to have Ubuntu and the games see my good card is question 1. Now running the games is not really possible either: with Oblivion (chipset for graphics) the intro movie crawled by so slowly, stuttering and devouring processor speed, that I never finished waiting for the menu to appear, and even shutting down the virtual desktop was not so easy. With Fallout 3 I got to the menu at good speed, although the LIVE button there only halted the animation, but when I tried to actually start a game, it crashed. And again getting out of the desktop is a hassle.

Ubuntu gurus out there, help. :popcorn:

---

### Post by temnix on 2010-12-23
About the Bethesda games: I have no Direct3D folder in Wine's registry.

---

### Post by cascade9 on 2010-12-23
Look in your BIOS, you might have an option to force the ATI GPU, or disable the Intel video (I wont dignify intel grpahics with the 'GPU' tag)

---

