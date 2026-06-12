---
title: "Is there a way to set GPU fan curve?"
date: 2016-08-12
forum: Hardware
---

### Post by disable2017Jul on 2016-08-12
In Windows, I set the custom fan curve for the GPU in Afterburner. Is there a similar software for that in Ubuntu?

---

### Post by CatKiller on 2016-08-12
Not that I'm aware of. Other fans can be controlled by fancontrol, but I don't think the GPU manufacturers expose that capability under Linux.

I think on NVidia cards you can control the current fan speed if you use CoolBits 4, but I don't think you can set a custom profile. It's possible that you could knock up some kind of fancontrol-like scripted solution (using nvidia-settings --query and nvidia-settings --assign) if you were game, though, I suppose.

---

### Post by disable2017Jul on 2016-08-12
> **CatKiller said:**
> Not that I'm aware of. Other fans can be controlled by fancontrol, but I don't think the GPU manufacturers expose that capability under Linux.

I think on NVidia cards you can control the current fan speed if you use CoolBits 4, but I don't think you can set a custom profile. It's possible that you could knock up some kind of fancontrol-like scripted solution (using nvidia-settings --query and nvidia-settings --assign) if you were game, though, I suppose.

I'm a noob so scripting is way outta my skills BUT I'd love to learn! Can you point me to the right direction where I could learn how to do this?

I know exactly what settings I want, it's a matter of translating that into scripts that the chip would understand.

---

### Post by CatKiller on 2016-08-12
I don't know either ;)

As I understand it, if you've got CoolBits 4 set in your xorg.conf, you'll be able to set the fan speed using the nvidia-settings command line utility. You can use the same utility to query the current temperature. So that handles the interface to the card.

Then you need something that will query the temperature of the card periodically and set the fan speed according to your curve. That's the bit that you'll have to do yourself.

This is exactly how the fancontrol utility works for the other fans in the system, so if you're keen to do it properly you could browse the source of that for inspiration.

Personally, I've found the default curve to be fine on my 960.

Also I suspect, but have no way to verify, that the curve can be stored in firmware by Windows utilities, so then it would still apply once you were in Linux.

---

### Post by disable2017Jul on 2016-08-15
> Personally, I've found the default curve to be fine on my 960.
I've no idea what the default fan curve of my 980ti is lol. I've always set my own one; they max out at 60C.

> Also I suspect, but have no way to verify, that the curve can be stored in firmware by Windows utilities, so then it would still apply once you were in Linux.
This is interesting....if this is a case, it would be AWESOME! I'm going to check this out and report back :)

---

### Post by CatKiller on 2016-08-15
> **teingyaminkhaung said:**
> I've no idea what the default fan curve of my 980ti is lol. I've always set my own one; they max out at 60C.

I don't think my GPU fan comes on at all below 60 °C.

> 
This is interesting....if this is a case, it would be AWESOME! I'm going to check this out and report back :)

Fingers crossed for you.

---

### Post by pqwoerituytrueiwoq on 2016-08-16
> **teingyaminkhaung said:**
> I've no idea what the default fan curve of my 980ti is lol. I've always set my own one; they max out at 60C.


This is interesting....if this is a case, it would be AWESOME! I'm going to check this out and report back :)
this will require using software to modify the firmware or BIOS on the gpu, i did this on my 650ti boost to OC it
nvidia does not make this software available to the public, this is reserve for card vendors to want to use non-default configurations (eg factory overclocks)
you will need to rely on 3ed party developers for this software

---

