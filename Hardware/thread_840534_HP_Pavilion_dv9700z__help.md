---
title: "HP Pavilion dv9700z  help"
date: 2008-06-25
forum: Hardware
---

### Post by madcowvt on 2008-06-25
Good day everyone. First time poster.
I have searched and still am not having any luck with a couple issues. Any help is greatly appreciated.

For the most part, Ubuntu is up and running (dual boot with Vista). Here are my main issues:

1. Despite researching (here and elsewhere) I cannot enable the 'fancy graphic options'. I have downloaded and attempted to install the proper Nvidia drivers without any luck. (64 bit driver is ok I assume? Have not tried 32 bit.)..I did exit X windows and ran as SUDO XX XXXXXXX.run. Said it needed to compile something, then said I needed some source files from installation but could not find them (not sure what they are now...sorry)

2. My understanding is that the built in NIC card should work. It does not. Nvidia chip set as well?)

3. The wireless card does not work either

If anyone can write a proper procedure list on how to install, tweak these items, that would be great. I have no experience with Ubuntu and would really love to get away from windows in general.

Here is my system:

- HP Pavilion dv9700z Entertainment CTO NB
- AMD Turion(TM) 64 X2 Dual-Core Mobile Technology TL-60 (2.0 GHz, 512KB+512KB L2 Cache )
- 17.0" WXGA+ High-Definition HP BrightView Widescreen Display (1440 x 900)
- 3GB DDR2 System Memory (2 Dimm)
- 256MB NVIDIA GeForce 8400M GS
- HP Imprint (Radiance) + Fingerprint Reader + Webcam + Microphone
- 802.11b/g WLAN
- FREE Upgrade to 250GB 5400RPM from 160GB 5400RPM!!
- SuperMulti 8X DVD+/-R/RW with Double Layer Support
- No TV Tuner w/remote control
- 8 Cell Lithium Ion Battery
- Microsoft(R) Works 9.0


Many thanks for any guidance!!

):P

---

### Post by madcowvt on 2008-06-25
Bump ^^

---

### Post by sergiom99 on 2008-06-25
please post the output of:
```
sudo lspci
```

so that we can see if NIC its recognized and how by Ubuntu. There's nothing in your specs about which chipset its on it.

---

