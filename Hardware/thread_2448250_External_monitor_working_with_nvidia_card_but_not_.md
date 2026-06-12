---
title: "External monitor working with nvidia card but not with intel"
date: 2020-08-04
forum: Hardware
---

### Post by elie2 on 2020-08-04
Hi,

I have the Levono Legion 7i with an nvidia RTX 2060. I installed ubuntu 20.04 and the nvidia 440 drivers. 
I'm trying to get a docking station working with two monitors. It's connected over USB-C. The dock is the Dell WD15.

In the nvidia settings, when I select performance mode/nvidia only, both monitors are working. When I select either hybrid or intel only I cannot get the monitors working. 

Is there a way to have the external monitors working with the hybrid mode? I would like to avoid having to reboot my laptop each time I wan't to play some games.

Thank you.

---

### Post by CelticWarrior on 2020-08-05
No, there isn't.

It has to do with the way the video ports are connected internally.
Vendors assume that if you're using an external monitor then you have access to an electrical outlet so you don't "need" the energy saving profile.

---

### Post by elie2 on 2020-08-06
> **CelticWarrior said:**
> No, there isn't.

It has to do with the way the video ports are connected internally.
Vendors assume that if you're using an external monitor then you have access to an electrical outlet so you don't "need" the energy saving profile.

That's what I was afraid of. It makes the switch between being plugged and taking your laptop with you less convenient. 

I saw USB 3.0 to HDMI Display Adapters, does that works the same way or is the OS creating some kind of virtual video ports?

---

### Post by CelticWarrior on 2020-08-06
If you're asking about DisplayLink based adapters they're independent from the other connections.

---

### Post by elie2 on 2020-08-12
I bought a USB-3 dock (Plugable UD-3900).
I got it working after installing the displaylink drivers.

The only issue, is a fps drop in games. On Tomb Raider benchmark I'm getting 44 average fps instead of 77 when playing with only the laptop screen.

It that to be expected? Is there anything I can do to improve that?

---

