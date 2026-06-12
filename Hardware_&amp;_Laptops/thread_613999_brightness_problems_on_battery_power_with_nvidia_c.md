---
title: "brightness problems on battery power with nvidia card"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by bobotoes on 2007-11-15
I'm running gnome gutsy on a laptop with an nvidia quadro nvs 140m using the nv driver _not_ the restricted driver. Running on battery power, my screen will dim much sooner than any settings in gnome-power-manager. I'd say, 30-60 seconds of idle (no keyboard or touchpad contact), and the screen dims to where it's difficult to read. This makes running on battery power very impractical. Is anyone having this problem / does anyone know of a solution?

---

### Post by f76 on 2007-11-23
Yes! on aspire 5920g i had some reasonable dimming maybe 80% brightness on battery power when i installed but i tried to *increase* the brightness on battery but now it is super dark on battery... And yes i have used the power management settings... Maybe there is a config i can delete/restore?

---

### Post by f76 on 2007-11-23
Forget it My mistake:lolflag: 
In the gnome-power-manager you set *brightness* for AC power
and *dimming* for battery power... so i set both to high and of course that explains why the screen was dim when i was on battery....

---

### Post by bobotoes on 2007-12-07
wow... somehow i misunderstood the settings in gnome power manager. I don't think the options are very clear especially since there so similar but so different to the AC tab. Oh well... fixed now... thanks for the reply!

---

### Post by jsully1 on 2007-12-07
In Gnome 2.20 (which ships with Gutsy) the option is backwards for On Battery Power - it's confusing, and in some languages it's not even translated right.
[http://ubuntuforums.org/showthread.php?t=581335](http://ubuntuforums.org/showthread.php?t=581335)

---

