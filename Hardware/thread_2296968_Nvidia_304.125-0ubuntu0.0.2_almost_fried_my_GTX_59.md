---
title: "Nvidia 304.125-0ubuntu0.0.2 almost fried my GTX 590"
date: 2015-09-30
forum: Hardware
---

### Post by discohr on 2015-09-30
Haven't been using my desktop lately and today I installed updates on it. After rebooting the screen was blank, went to text mode and lower part of the screen was glitching. Rebooted again and BIOS screen was full of glitched red lines. Switched PC off immediately, waited a bit then switched it back on and everything was fine so I booted into single user mode and reverted back to 0.0.1. Works perfect now.

Does anyone actually test these updates on the actual hardware before releasing them?

I will not post a bug report because I'm not willing to risk my card further while gathering logs.

Why I'm not using the latest driver? Because it doesn't work, obviously. Tried 346 today, it gives "out of sync".
Nouveau always freezed this PC on Ubuntu. I was lucky to install Ubuntu at all without freezing several years ago, took me about 5 tries. I had no issues after removing Nouveau, until now.
Fedora was the only distro that had no issues at all with this PC (even Nouveau worked) but I switched to Ubuntu years ago and I'm not going back.

Relevant hardware specs: Intel DX79SI board, Intel 3930k CPU, 32 GB RAM (1600 IIRC), Nvidia GTX 590, Asus VE276 monitor.

EDIT:
Forgot to mention it was on 14.04 LTS.

---

### Post by dino99 on 2015-09-30
*******  BIOS screen was full of glitched red lines ************
that's enough to explain it is not a graphic driver issue.
is your hardware working with stock specs ? or have you made some overclocking or powering tweaks ?

---

### Post by discohr on 2015-10-04
Nvidia was never overclocked. It's an old card but still powerful today, there is no need to overclock it. I believe the driver update overclocked it and that resulted in glitched red lines on BIOS screen after CTRL+ALT+DEL. Can't imagine why would a driver overclock the card by default, it's not supposed to do that. Can't explain why latest nvidia driver in Ubuntu is messing with monitor timings either. In all cases Ubuntu was the only OS booted, there was no "Windows was booted first and left hardware in weird state" situation. Everything works fine in both Ubuntu (with selected driver version) and Windows (all driver versions), no glitches or anything.

EDIT:
Installed 346.96. Screen is blank. Dmesg output is attached, looks like nvidia driver crashed.
[ATTACH]264811[/ATTACH]

EDIT2:
Nevermind, just happened again after cold boot. My 590 is dying. RIP.
[ATTACH=CONFIG]264813[/ATTACH]

EDIT3:
Replaced HDMI cable just to make sure it's not cable's fault, everything is ok, even with 346.96 in Ubuntu!
Inbetween original post and first edit I ran FurMark burn-in test for 30 minutes, no problem at all. Surely, card wouldn't work perfectly if it was dying.

Sigh, don't know what to think after all this. I wish it either works all the time or dies so I can buy 980. One thing is sure: it's never boring in the Twilight Zone.

EDIT4:
It was the HDMI cable after all. No issues since I changed the cable.

---

