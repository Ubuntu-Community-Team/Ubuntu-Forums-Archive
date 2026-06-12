---
title: "Creative Audigy 2 ZS and Feisty Herd 3"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by lamalex on 2007-02-07
I recently upgraded to start testing feisty fawn to see if network-manager worked better under it (which is does). but in doing so my sound card no longer works? My onboard sound through my notebook speakers works fine, and ubuntu sees that I have an Audigy card plugged in but even if i select it sound still comes out of my notebook speakers and not my surround sound. yes they work i general, I tested them in windows.
notebook is an HP DV5139US soundcard is Creativelabs Audigy 2 ZS notebook.
thanks for any help! I'm stumped.

---

### Post by bionnaki on 2007-02-08
run alsamixer and see if any meter has been lowered. and check to see if Audigy Analog/Digital Output Jack is turned off (to turn on press m).

typically you need master, pcm, front, and audigy analog/digital ouput turned on for the audigy to work in alsa

---

### Post by lamalex on 2007-02-08
> **bionnaki said:**
> run alsamixer and see if any meter has been lowered. and check to see if Audigy Analog/Digital Output Jack is turned off (to turn on press m).

typically you need master, pcm, front, and audigy analog/digital ouput turned on for the audigy to work in alsa

alsa mixer is showing my notebook's internal as the output, how do i change it?

---

### Post by bionnaki on 2007-02-08
you should probably disable your onboard sound if you want to run your other soundcard. having both enabled is confusing your laptop...and making things complicated. no need to have onboard enabled if you have and want to use the audigy.

disable via your bios.

---

