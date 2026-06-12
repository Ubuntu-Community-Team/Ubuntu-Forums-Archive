---
title: "failure on HP Laptop"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by Devilotx on 2006-11-08
So I purchased a new laptop to replace my "Old" laptop, my old lappy was nothing to sneeze at, but the integrated ATI mobility card was crap.

So I just bought an HP dv6110us, Turion X2 (1.6), with a gig of ram and 100 gig drive and a Geforce Go 6150

I've installed Ubuntu Edgy with the Desktop installer, everything seems to be ok. but on reboot, I get a garbled screen that slowly fades into pure white (almost looks like my LCD is superheating/melting)

this has happened everytime.

Not sure what to do, the xorg.conf is conservative, 1024x768, and either the vesa or nv driver.

Any help would be appreciated.

---

### Post by justifier on 2006-11-08
Could it be afaulty screen? mybe? just a possibility. does it happen when you run a liveCD?

---

### Post by happy-and-lost on 2006-11-08
I *think* you need to use the x86_64 edition of Ubuntu on a Turion.

---

### Post by Devilotx on 2006-11-08
I do get some Corruption where the ubuntu logo would be with the bar rolling below it, although that does show up fine, it just distorts right before it loads the desktop.

The desktop comes up fine (I have to use safe graphics to get it to come up)

this laptop is literally 1 day old, the screen works fine in the Windows XP Media Center install on the first partition.

and X64 is not required, I'd prefer not to use it as well.

---

### Post by Devilotx on 2006-11-08
Seems like Passing acpi=off seems to allow this to boot the nv kernel, going to try the nvidia kernel now.

However this seems to kill the sound,

---

### Post by Devilotx on 2006-11-08
Alright! I've fixed it

the NV driver in Edgy's Sources would fail, no gui.

I installed the latest beta nvidia driver and BAM!

everything is good as gold, I get Gui, I get sound, I get everything.

---

