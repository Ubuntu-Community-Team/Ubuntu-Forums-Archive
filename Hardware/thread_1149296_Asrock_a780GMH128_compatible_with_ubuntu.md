---
title: "Asrock a780GMH/128 compatible with ubuntu?"
date: 2009-05-05
forum: Hardware
---

### Post by afonteijn on 2009-05-05
I'm thinking about buying an asrock mobo (a780GMH/128 ). I haven't been able to find any reviews describing if and how it works on linux. So... does anyone know if this mobo will run well with ubuntu 9.04 (or earlier?) 
It features the following:
[LIST]
[*]AMD 780G + SB710 Chipsets
[*]Integrated AMD Radeon HD 3200 graphics
[*]PCIE Gigabit Realtek RTL8111DL
[*]VIA® VT1708S Audio Codec with QSound
[/LIST]

Any input would be great!

---

### Post by atomizer on 2009-05-05
A bit of google on your hardware + keyword "ubuntu" shows that there could be a problem with your network and sound in linux.

---

### Post by afonteijn on 2009-05-05
Atomizer, thanks for your reply. I think that most of the problems with the sound and network card have been solved in ubuntu 9.04. However, from experience I know that motherboards with virtually the same specs sometimes run differently in ubuntu. So, if anybody is running ubuntu with this mobo... please let me know!

Btw, how well is ATI being supported in ubuntu by now. I want to buy an ATI card because they seem to be developing semi-open source drivers. However, how is their current compatibility with ubuntu and their performance (specifically compiz)?

---

### Post by alizard on 2009-06-21
Network problem is no big deal... if it doesn't open your network, try

$ sudo dhclient

then run
$ sudo ifconfig 

and change /etc/network/interfaces to match whatever it reports your ethernet connection as.

As for video, I simply downloaded and ran the ati binary... and aticonfig from a terminal as the program output recommended. NO problems, other than that the OpenGL setup isn't optimized, getting under 800 fps on glxgears.

The audio driver setup is a trainwreck... the fix may be to patch and recompile the alsa subsystem. I am getting NO speaker or headphone output at all. 

But I'm looking for an easier fix. If audio is important to you... it's a nice motherboard, but this should be a dealkiller for you until this is fixed. 

If it isn't... I'd say buy it and keep an eye out for a new VIA1708S driver or an ATI SBx00 Azalia (Intel HDA) driver solution or even a snd-hda-intel config option that works. While the driver is nominally snd-hda-intel ... it is seen by pulseaudio and appears working... but no sound comes out. 


While this is based on a Debian testing distro I just upgraded to KDE4.2.x, the audio problem reports with this motherboard I base this on are straight from ubuntu sites.

---

### Post by Lampi on 2009-07-21
@afonteijn: The board works fine with jaunty, onboard NIC and audio won't work with Debian/Lenny or any other distro using kernel 2.6.26. So Kernel 2.6.28 is required.

---

### Post by afonteijn on 2009-07-25
Thanks for all the replies. I finally decided to avoid ATI and go with an onboard nvidia geforce 8300 video card. It is the asus M4N78 PRO and it works well with Ubuntu 9.04 and Fedora 11. Most of the problems I encountered were related to using a 64 bit os. I definitely can recommend this mobo for linux users. (There are even sound drivers for linux available on the asus cd - not that I used them - but that is pretty amazing!)

---

