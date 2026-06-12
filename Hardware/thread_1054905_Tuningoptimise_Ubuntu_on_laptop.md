---
title: "Tuning/optimise Ubuntu on laptop"
date: 2009-01-30
forum: Hardware
---

### Post by Xyem on 2009-01-30
I think it is pretty safe to say that the hardware in my laptop won't change so I was wondering if there was a howto on how to optimise for this laptop? For example, stop probes for hardware ( as it will never change ) and explicitly say what hardware there is to minimise boot times.

Any pointers?

---

### Post by sdennie on 2009-01-30
It's possible to do this but, at most it will speed up your boot time by 1-2 seconds.  It sounds like you want to do what this link describes [http://wiki.archlinux.org/index.php/Speedup_udev](http://wiki.archlinux.org/index.php/Speedup_udev)

---

### Post by kerry_s on 2009-01-30
> **Xyem said:**
> I think it is pretty safe to say that the hardware in my laptop won't change so I was wondering if there was a howto on how to optimise for this laptop? For example, stop probes for hardware ( as it will never change ) and explicitly say what hardware there is to minimise boot times.

Any pointers?

what laptop?
does suspend and hibernate work? suspend gives you instant on, hibernate can cut the boot in half.

disable the logs you don't need, just # them out. (sudo gedit /etc/syslog.conf (i think, i'm in arch, it's different))

disable unneeded services.

switch to a window manager, it's faster, lower resource, gives you more control over whats running.

use lighter alternative programs.

disable aiglx and composite. it will cut X memory use down. i also renice it to a higher priority for more responsiveness. 
in .xinitrc i have: sudo renice -5 -p `pidof X` &&
it would be `pidof Xorg` on ubuntu/debian, also don't forget to add renice to your visudo NOPASSWD.

my laptops only 450mhz 256mb ram, i install mine optimized from the get go, i start with a base install and just build up from there, just installing what i actually use.

i been up a day and still ain't in swap yet. ;)

---

### Post by Xyem on 2009-01-31
sdennie, thanks, I'll look into that.

kerry_s,
**what laptop?** Acer Aspire 5930 ( 2Ghz, 3GB RAM, 220GB SATA, GeForce 9800M GT )
**does suspend and hibernate work?** Suspend works but mitigates my disk encryption. Hibernate doesn't work ( because swap is encrypted ).

**switch to a window manager:** Already running Fluxbox because GNOME has become too much "take control over everything"-y for my tastes ( and it starts really slowly.. something I've noticed since Intrepid )

**i start with a base install and just build up from there, just installing what i actually use.** I will be doing this with Jaunty. I tried with Intrepid but couldn't get various things working.

Thanks for the tips :)

---

