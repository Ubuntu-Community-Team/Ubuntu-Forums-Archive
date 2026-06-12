---
title: "Still no sound"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by mimitam on 2009-09-02
I installed the ubuntu 9.04 built in Volume Control App, PulseAudio. I unmuted and adjusted all the nobs and buttons but still no sound. This is a dual-boot laptop with Vista. Sound works just fine in Vista.

Any suggestions on what I should check or do next to fix this problem?

Many Thanks...Mimi

---

### Post by kevinatkins on 2009-09-02
Hi Mimi,

Could you provide a bit more information please - what sort of computer are you running (make / model etc..)

---

### Post by Luca_turicci on 2009-09-02
Need Hardware info

In the meantime, try installing all updates available

---

### Post by mimitam on 2009-09-03
I am running Vista and Ubuntu dual-boot on a Dell Inspiron 1521 laptop.

Sound device driver in Vista which works fine is the SigmalTel High Definition CODEC.

In Ubuntu, I tried to configure device driver as SigmaTel STAC... (OSS Mixer) and Ialso tried Playback: HDA ATI SB - STAC92xx Analog (PulseAudio Mixer), to no avail.

How can I determine which device driver Ubuntu should use if there is not a  mdevice name same as in the Vista's?

Other than that, what else should I check? I must be missing something else as well.

Many Thanks...Mimi

---

### Post by Luca_turicci on 2009-09-03
Hope this works

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

