---
title: "No sound with Gigabyte H55M s2 motherboard"
date: 2010-11-15
forum: Hardware
---

### Post by neerajnabar on 2010-11-15
Hello everyone,

This is my first post on the forum. I've been trying to configure the audio on my desktop PC since the past two weeks, but without any success. I had installed Fedora 13 on my PC after upgrading to a new motherboard and processor (i've put the specs at the end), and **the audio was working just fine**. However a few days later when I booted into F13 there was no sound, so i decided to install Ubuntu 10.04 instead, and yet there was no sound.

Here are the relevant PC specs:

[B]Gigabyte H55M - S2 (v1.3) with the on-board audio setup as
1. Realtek ALC888B codec
2. High Definition Audio
3. 2/4/5.1/7.1-channel
[/B]
**Intel Core i3 530 processor (2.93 GHz).**

**Ubuntu 10.04 dual boot with Windows 7 Ultimate**

Also, when i run the usual commands for troubleshooting i get the following.

~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ alsamixer
cannot load mixer controls: Invalid argument

Notice that aplay discovers an ALC887 codec while the on-board audio has a Realtek ALC888B codec. Is the motherboard compatible with this version of Ubuntu? Are there any third-party drivers available for download on the Web? I have seen a few posts here with the same problems, but I guessed I would put this in a new thread because there was sound on F13 at least

Any help would be greatly appreciated. I am a sworn fan of Ubuntu and it is disappointing to see everything else go smoothly except for the total absence of sound :(

---

### Post by sivamgr on 2010-11-30
Go to Terminal

add the following line to /etc/modprobe.d/alsa-base.conf

> options snd-hda-intel model=genericand restart ubuntu

---

### Post by d22901 on 2010-11-30
sivamgr's method works on my Gigabyte M68MT-D3 board with NVidia MCP61 HD chip for both output and (more importantly) input.  I had all sorts of problems trying to get the mic/line ins to work on this board.  Did have success getting output to work.

That said, using model=generic gives me no SPDIF out option, which is critical for me.  I'd assume there's no way to get this enabled (yet)?

EDIT: Check that, only the rear mic input works.  Line-in and front mic input do not work, although the front headphone output works.

EDIT 2: Not exactly sure what happened (update?), but using model=auto suddenly works with gamix.  alsamixer and gnome-alsamixer still fail, but gamix loads (with two instances of: probe.c 168: control info read failed: Invalid argument *however, GUI loads fine).  All ins/outs, including front mic/headphone jack and SPDIF functional.

---

