---
title: "HDMI Audio on Nvidia 319.60 prop driver. [13.10]"
date: 2014-04-14
forum: Hardware
---

### Post by matrix89672 on 2014-04-14
Heya everyone,

I'm sure thie question is asked 70,000 times a day. But I'm sick of booting back and forth between operating systems anytime I want to watch anything...

HDMI Audio in my Nvidia GTX580 is a no go. Has been since 12.10. Using Prop Driver 319.60.

I'm a total noob, but I did manage to look in the alsamixer, and it reported back that it sees my HDMI channels...but won't do anything with them.

I've been looking for a solution for this since 12.10, and have yet to find anything. It'd finally irked me enough that I'd ask for help...

I've attached a screen shot of my alsamixer.

Everything I've seen for the past few years has been: "hm. It's broke."

So, I'll post back with any outputs/sysinfo needed. This is driving me up the wall.

[ATTACH=CONFIG]252074[/ATTACH]

Please and thanks.

---

### Post by trag on 2014-04-15
download grub2customizer, under general settings change "quiet splash" to "quiet splash nvidia=audio1"or "quiet splash radeon=audio1" for some reason HDMI audio is disabled by default and must be activated via the kernal,using pavucontrol select Digital Stereo(HDMI)Output
good luck
trag

---

