---
title: "Hardware Compatibility"
date: 2006-05-09
forum: Hardware &amp; Laptops
---

### Post by Micro$oftWinblows on 2006-05-09
I've a friend who wishes to run Ubuntu on a desktop computer. They'd like to take advantage of the image, sound and video editing software available on Linux platforms.

The computer setup is as follows:

ASUS P5LD2 Delux (Intel 945) Mother board with a Pentium 4 3.2G (640) CPU.
1GB Dual-Channel DDR2 RAM (533Mhz)
NVIDIA GeForce 6600 LE or ATi Radeon X550 PCI-Express card
200G Serial ATAII Hard Drive

(peripherals are plug and play, I'm guessing they'll be supported).

The motherboard comes with integrated surround sound, gigabit ethernet, 54mps 802.11G wireless.


Will all this be compatible with Ubuntu?

---

### Post by Monster_user on 2006-05-09
[QUOTE=Micro$oftWinblows]with a Pentium 4 3.2G (640) CPU.
1GB Dual-Channel DDR2 RAM (533Mhz)[/quote]
Incompatibilities with Pentiums, and RAM, are usually hardware related. I've never heard of any problems with these.

However the motherboard is fairly new, and uses the i945P chipset. That has me concerned.

[QUOTE=Micro$oftWinblows]NVIDIA GeForce 6600 LE or ATi Radeon X550 PCI-Express card[/quote]
OR??? That is a BIG "or". If you got that off of a website, then I HOPE he has the NVidia. If you meant that is the choice, NVidia cards usually work without issues. ATI cards often work, but without any fancy effect support. With an ATI card, don't expect to have shadows, transparencies, or 3D screensavers, or games.

[QUOTE=Micro$oftWinblows]54mps 802.11G wireless.[/quote]
This WILL require a recent version of NDiswrapper. 

[QUOTE=Micro$oftWinblows]Will all this be compatible with Ubuntu?[/QUOTE]
It is compatible with Ubuntu 6.06 - Dapper Drake (release date June 2006). I do not know about Ubuntu 5.10 - Breezy Badger  though.

The good news is that the board is supported by relatively new distros. Suse 9.2, Fedora Core 3. Breezy should work, but there may be issues. Here is a compatibility report.

[http://www.linux-tested.com/results/asus_p5ld2.html](http://www.linux-tested.com/results/asus_p5ld2.html)

---

### Post by aysiu on 2006-05-09
This is where live CDs really come in handy.

---

### Post by Micro$oftWinblows on 2006-05-09
Thanks for your replies.

[http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8756/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8756/README/appendix-a.html)
The NVIDIA GeForce 6600 LE is listed here - I'm assuming that means there's a Linux driver for it.

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI) This mentions X series cards, I'm also assuming that covers the ATi Radeon X550 PCI-Express card.

As for the Live cd comment... I wish I could test it out but the computer is yet to be purchased. I just don't want my friend to purchase the computer and find that it's not compatible with Ubuntu.

---

### Post by Monster_user on 2006-05-10
It looks like I accidentally removed my comment about the SATAII drive.

Linux has limited support for SATA controllers. I don't know if it supports SATAII at all. If it doesn't, then you will not get the full SATAII effect, whatever that may be.

If I had to guess at this point. I don't like guessing,... I would have to say that it is not compatible with Breezy. 

Dapper *Should* work.

YES, the NVidia card is supported by every current distro. You should have NO problems with it.

The ATI card, while it is officially supported, may not yield the same results. ATI users often have to do a lot of manual changes, to get the same level of functionality out of an ATI card.

You will not be able to get window drop shadows, most transparencies will not work, nor will the Xgl 3D desktop. Also, 3D software usually runs slower on an ATI in Linux. Well, this stuff may work with a bit of work.

A basic, bland Ubuntu installation will work without any hiccups on an ATI card.

Go with the Geforce 6600 LE.

---

