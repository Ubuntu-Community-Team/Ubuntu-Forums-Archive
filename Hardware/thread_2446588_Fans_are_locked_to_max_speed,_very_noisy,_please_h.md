---
title: "Fans are locked to max speed, very noisy, please help"
date: 2020-07-03
forum: Hardware
---

### Post by lxme on 2020-07-03
Hello everybody,

My computer started to act weird a few weeks ago, making a lot of noise.

It turned out it was my Nvidia GT760 fans spinning to max speed (from login screen precisely). I’am unable to make them go slower. Temperature is detected by Nvidia X server settings, but speed is not in Thermal settings and Fan 0 Speed is greyd out.

GPU Temperature is low, but noise is very high. It’s my main work desktop and my ears are being destroyed, please help.

What I tried:

- Changed to older kernels: no go, fans maxed out
- switch to nouveau driver: fans act normally
- run from live CD: fans act normally
- tried different ubuntu Nvidia drivers (340,415,435): no go, fans are maxed out

I’m running ubuntu Ubuntu 18.04.4 LTS

Any ideas on what I could do is welcomed.
I’m not even sure this is software or hardware problem. If happend a few days after I clean my computer case, so maybe I damaged something? But then again, why would other drivers keep the fans in control where Nvidias own drivers can’t ?

---

### Post by TheFu on 2020-07-03
Replace the fan. There are probably nearly silent replacements for $10 and quieter fans for $20.

---

### Post by lxme on 2020-07-03
Hello

"They are probably nearly silent"

word missing? "dead" ?

Fans are working just fine, they are just going full speed with NVIDIA drivers
this doesn't happen with nvidia nouveau driver.

I'd say there is a problem with the driver or the fan sensor is misbehaving
But I need help to determine what's wrong

---

### Post by CatKiller on 2020-07-03
> **lxme said:**
> Temperature is detected by Nvidia X server settings, but speed is not in Thermal settings and Fan 0 Speed is greyd out.

There's a coolbits setting you have to apply elsewhere to enable fan control through Nvidia settings.

---

### Post by lxme on 2020-07-04
Ok thanks for your help guys, but I found a solution.

It was NOT software.

One of the two GPU fans on the card was stuck, forcing the second one to spin full speed to compensate.
A gentle nudge on the stucked fan made it spin again and the first one quicly slowed down to normal speed.
Problem solved.

---

### Post by mastablasta on 2020-07-06
[COLOR=#000000]Nvidia GT760 - isn't the last driver 3.90 something to support the 700 series?[/COLOR]

---

