---
title: "PC, Memtest86+ hangs: what to do?"
date: 2023-03-11
forum: Hardware
---

### Post by Nickolai_Leschov on 2023-03-11
My PC running Ubuntu 20.04 LTS started hanging in random moments, after I brought it with me on an international plane (it's in a tiny mini-ITX case, so I took it with me as hand luggage and handled with care).

When I boot Memtest86+ from GRUB, it starts but hangs at 1 second mark without showing any error. The red '[COLOR=#ff0000]+[/COLOR]' symbol continues flashing perpetually, but the program stops running and doesn't respond to key presses anymore. In Safe Mode the result is unchanged. There are two DDR slots on the motherboard, populated with identical Kingston memory modules. I have tried removing them and installing back, one by one, in all possible combinations (one module, two modules...) to no effect.
I tried fiddling with BIOS, in particular resetting it to optimized defaults (just because I see no option to reset to regular defaults) and back, manually, to no effect.
Changing between the discrete and integrated GPU has no effect. So does disconnecting all the non-essential peripherals.

What is likely the matter? **What should I do to fix my PC?**

Here's my take: it's probably the motherboard that is broken somehow (socket?) and has to be replaced. Just because the CPU is pretty sturdy and hard to break when it's properly socketed and RAM defect is out of the question by testing. Am I right?

[IMG]https://i.imgur.com/yY9r5eO.jpg[/IMG]

_Here's the computer's specs, just in case:_
**Case**: NCASE M1 v5.0
**PSU**: Corsair 600W 80 Plus Platinum
**MB**: ASUS H81I-PLUS
**CPU**: Intel Core i7-4770S
**Cooler**: Be Quiet! Shadow Rock LP
**RAM**: 2x8GB Kingston PC3-1333
**SSD**: Samsung 860 EVO 250GB
**VGA**: MSI GeForce GTX 1050 Ti GAMING X 4G
**Extras**: E-MU Tracker Pre USB2.0 soundcard, Logitech C920 webcam, D-Link USB2.0 active hub which I disconnect for testing.
Ubuntu 20.04 LTS with Unity installed.

---

### Post by guiverc on 2023-03-11
I can't provide anything beyond my own experiences, but maybe it'll be helpful.

I have boxes where memtest86 as provided by Ubuntu (*or Debian in fact*) just hangs..  When I discovered this I was worried the box [a], so I swapped RAM with another box [b] & performed tests again.. The other box [b] passed all RAM with 3+ full scans, but the memtest86 on box [a] still hung.

I returned the RAM to their original boxes; ran memtest a week on box [b] & spent a week testing box [a] looking for issues but found none.  I finally decided box [a] was reliable/trustworthy.

Since then I've found other boxes where memtest86 doesn't work, so I don't use it as an indicator of problems UNLESS I know that box/motherboard/firmware combination has run it in the past without issue. 

FYI: I did find trying older *live* media I could find occasionally get different behavior with memtest86 on those boxes; but it was inconsistent; and possibly related to uEFI/BIOS settings... I just decided to rely on the inbuilt RAM tester for those boxes if I didn't want to swap RAM between boxes (*which I'll do if I consider I have a real problem*)

Summary:   If it was me, if you don't know that memtest() reliably runs on that box, I'd not be worried.

---

### Post by Nickolai_Leschov on 2023-03-13
Thank you very much for sharing your experience, **@guiverc**!

This and advice by another member of another forum made me install and try the latest version of Memtest86+, the v6.10.
[It doesn't hang]("https://i.imgur.com/XOZTBuG.jpg")! While [the v5.01 still does]("https://i.imgur.com/FCmgnL0.jpg") (<- new screenshot here)

Sadly, the PC still does hang.

What could be the matter?

---

### Post by guiverc on 2023-03-13
The *likely obvious* things I'd check are 

- visual scan (cap check etc); ie. visual signs that components are *dying* such as *swollen capacitors *etc.
- good connections, good cooling etc.. (been kicked? dropped etc? or if hidden away in a garage etc. ensure no spiders have made a home in it which can severely impact the cooling etc)
- check PSU; even good components will *misbehave* if fed incorrect power

ie.   for me I'd explore hardware.

---

### Post by Nickolai_Leschov on 2023-03-14
The thing came to my mind: why is my RAM working if it's **ECC**? Should ECC RAM work at all? Don't remember why I bought ECC specifically; maybe the seller didn't advertise the fact? Definitely the price was good and it worked.
I have originally assembled this PC from the used parts (except for the cooler) and one thing I know is it did work well for well over a year, pretty intensively at times (played through 3xDiablo II Resurrected), casually browsing at others, and it didn't hang. Also, I did run Memtest86+ after installation.
Now it hangs.

For now, I decided to risk it and upgrade the BIOS from version 0707 to 2305 (H81I-PLUS-ASUS-2305.zip). If it ain't broke, don't fix it, I decided originally, but now that it did broke...
The upgrade went smoothly, testing now.

---

