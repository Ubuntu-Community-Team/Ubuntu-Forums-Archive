---
title: "boot error (hw_random)"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by invictus on 2005-01-22
When I boot my warty system I get the following message;

Modprobe: FATAL: Error inserting hw_random (/lib/modules/2.6.8.1-3-386/kernel/drivers/char/hw_random.ko): No such device

As far as I know my chipset (intel 865G) support RNG (random number generator) so I dont get this. Any ideas?

---

### Post by shmonkey on 2005-01-23
This is from Debian

> On Thu, 2004-06-24 at 14:17, oscar wrote:

> hw_random: RNG not detected
> modprobe: FATAL: Error inserting hw_random 
> (/lib/modules/2.6.5-1-686/kernel/drivers/char/hw_random.ko): Not such device

This just means the system tried to load the hw_random module, but since
your system doesn't have a built-in hardware rng it can't load it.

Just remove the hw_random entry from /etc/modules*

AFAIK hw_random devices are in some via C3 chips, intel's i810 chipset
and some P4 chips

Mark 

---

### Post by Buffalo Soldier on 2005-01-23
[QUOTE=invictus]When I boot my warty system I get the following message;

Modprobe: FATAL: Error inserting hw_random (/lib/modules/2.6.8.1-3-386/kernel/drivers/char/hw_random.ko): No such device

As far as I know my chipset (intel 865G) support RNG (random number generator) so I dont get this. Any ideas?[/QUOTE]Here's a links to a list of websites that you can go through to search for solutions. [http://ubuntuforums.org/showthread.php?p=54189](http://ubuntuforums.org/showthread.php?p=54189)

But for the specific problem you have now, here is what I would suggest: [http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

---

