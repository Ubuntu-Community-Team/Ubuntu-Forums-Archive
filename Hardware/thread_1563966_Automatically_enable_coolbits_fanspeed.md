---
title: "Automatically enable coolbits fanspeed"
date: 2010-08-29
forum: Hardware
---

### Post by cswenson on 2010-08-29
I have a Nvidia 9800GTX+ running on my Lucid installation.  I have Coolbits enabled and have manually increased my fan speed (it runs hot if I don't).

My question is this:  Whenever I reboot the computer (or even restart X), I have to manually open the Nvidia settings under 'System'->'Admin'->'Nvidia X Server Settings' and click a stupid check box saying that "Yes I know what I'm doing and want to enable this feature.....blah, blah, blah" all just to increase my fan speed.  As far as I can tell there isn't any way keep the box checked.  It appears not to effect the ~/.nvidia-settings-rc file, or my xorg.conf file.  Somewhere something must be changing that allows me to access the fan controls, I just don't know where.

Does anyone know how I can permanently keep the box 'checked'?  What file is being written to, does anyone know?  Once I check the box, I can use the CLI for nvidia-settings to adjust my fan speed, and I have some cron jobs that automatically adjust the fan speed based on the temperature of the card.  The only things keeping from having a completely automated GPU fan is the stupid checkbox!

Has anyone figure this out before?

Thanks.

---

