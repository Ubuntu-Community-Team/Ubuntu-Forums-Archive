---
title: "HD audio powersave in ubuntu lucid, is it broken ?"
date: 2010-05-09
forum: Hardware
---

### Post by Axx83 on 2010-05-09
Hi guys, since having newly installed lucid everytime I run "powertop" it says my HD audio card is not in powersave mode:

An audio device is active 100,0% of the time:
hwC0D0 Analog Devices AD1981

Suggestion: enable HD audio powersave mode by executing the following command:
   echo 1 > /sys/module/snd_hda_intel/parameters/power_save 
or by passing power_save=1 as module parameter.

this did not happen with karmic...what is the problem?

I checked the module and there is no parameter anymore, but pm-utils has a new script that should put the card in powersave but it doesn't

---

### Post by paol05 on 2010-05-09
Hi. I can confirm the same thing on my laptop (Thinkpad T500)

---

### Post by Axx83 on 2010-05-09
I got a reply from the author of the pm-utils script:

___________
> My card is a hda intel codec AD1981

By default in Lucid, the ten-second idle timeout only takes effect if
the following conditions are true:
1) you use a Sigmatel/IDT HDA codec;
2) you use battery power (not plugged into an outlet).

Since your codec is an Analog Devices and not a Sigmatel/IDT, the
powerdown is not done.
___________


Looks like there's nothing to do. Personally I reinserted the module option in alsa-base.conf

---

### Post by frankvielma on 2010-05-25
Hi

I can confirm too the same thing on my Desktop running Ubuntu Lucid, kernel 2.6.32-22-generic, Intel Corporation 82945G/GZ/P/PL.

---

