---
title: "Feisty on Dell Inspiron 9400"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by GeneWine on 2007-05-04
Hi.

I first want to say hello to the community as of my first post.

I am a Gentoo Linux user and I have tried Ubuntu (since 5.04) on my company's laptops as soon as I had an opportunity. Feisty is the first Ubuntu that seemed to work with every laptop I have tried until now. I must admit everything works like a charm: the video driver, SD card reader, function keys, WiFi, network management.

Honest Feisty is the best Ubuntu achievement. That's my opinion. As I'm not a Debian/Ubuntu regular user there are still things I could not do like playing video/audio files in proprietary formats like MP3 and DivX but that's not the purpose of my post - I can figure it out by myself later on.

I am using Gentoo as my regular distribution and there are two major points where I'm stuck: the built-in Ricoh SD card reader and the ipw3945 Wireless. These work as expected in Feisty: when a SD card is inserted in the reader, KDE prompts for mounting it; ipw3945 also works with the latest driver and daemon, i.e. udev loads the driver and the regulatory daemon starts immediately.

Using the same versions on Gentoo doesn't seem to work as in Feisty.

[LIST][*]**Ricoh SD Card reader**: I have to mount an inserted SD card manually for KDE doesn't prompt for the "New media detected" dialog.

[*]**ipw3945**: the latest firmware (**1.14.2**) and daemon (**1.7.22-r4**) do not work together with the latest version of udev (**109-r1**).
Under Gentoo udev loads the driver but the daemon exits saying "*Could not find Intel PRO/Wireless 3945ABG connection*" although the driver module exactly says the contrary. I have had to downgrade the daemon (**1.7.18**) and firmware (**1.13**) but I also had to use a script of my own to have the daemon properly loaded when udev inserts the driver module - ipw3945d **1.7.18** was not yet aware of udev.[/LIST]
Hence since these two things work properly in Feisty I wondered if there was something special to know or do about them. (Note automounting unders Gentoo doesn't work only with the SD card for it does work with USB aso.)

Here are my specifications:
[LIST]
[*]Kernel (Gentoo sources) 2.6.20-r7
[*]udev 109-r1
[*]ipw3945 1.2.0
[*]ipw3945d 1.7.18
[*]ipw3945-ucode 1.13
[*]KDE 3.5.5
[*]SD card driver modules: built-in sdhci (from Pierre Ossman), mmcblk[/LIST]
I am not asking for Gentoo support. I'm just wondering why these two pieces of hardware work right out the box under Feisty and what has been done under Feisty to make them work. I'd like to understand what I have to do to have these pieces of hardware work alike in my favorite distro.

Thanks in advance.

---

