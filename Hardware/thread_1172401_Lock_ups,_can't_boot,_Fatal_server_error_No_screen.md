---
title: "Lock ups, can't boot, Fatal server error: No screens found"
date: 2009-05-28
forum: Hardware
---

### Post by yaroto98 on 2009-05-28
I'm running 9.10 on my laptop, and have been doing some pretty fun Wine gaming on it.

HP Pavilion dv2000
Centrino Duo
2GB RAM
Nvidia GeForce 8400M GS

And ever since I upgraded to 9.10 whenever I shut down, the screen tiles for the last stage. But there never was anything wrong aside from that, so I just ignored it. However, just today, it kept locking up while playing some video games. It'd lock up hard, no key combinations would work, and after rebooting it a few times, I gave up on the game and was just surfing the internet.  Well, it locked up with just firefox open, and the screen was flashing at me for about 30 seconds before it stopped. Now I can't boot up. When I boot, the display starts out tiled (bios screen, grub screen) and when I get to the ubuntu stuff it seems to go though the boot process just fine, but after the loading screen finishes, the login screen never pops up. I checked out a few bios diagnostic tests, and everything comes back normal. Then I booted into the recovery thing ubuntu has, and it passed all of them.  I even ran the auto fix display settings tool thing.  I went to the "boot normally" and it brought up an error, and I looked at the xserver log, and at the bottom it says:

```
Output LVDS connected
Unable to find initial modes
Output LVDS enabled but has no modes
No valid initial configuration found
Unloaded Module: "nv"
Unloaded Module: "int 10"
Unloading /usr/lib/xorg/modules//libint10.so
Fatal server error: no screens found
Screen(s) found, but none have a usable configuration
```

Maybe when I rebooted it corrupted a file?
(also I can't be too sure about the spelling of everything above, the tiled screens makes everything squished and hard to read)

---

### Post by yaroto98 on 2009-05-28
*UPDATE*
After messing around in the recovery console, I was able to start up ubuntu in a "Low Graphics Mode", however no matter what I do the screen is still tiled. (about 6 of them on the screen) Could this be something as simple as a loose display cable inside my laptop? I can't think of anything else that would tile the display for everything, even the bios screen.

---

### Post by yaroto98 on 2009-05-28
Never mind. For once in my life the removing the RAM and putting it back in trick worked. All fixed.

---

### Post by yaroto98 on 2009-05-28
Yea, nix that previous one. It happened again, I tried to recreate every step I went through, and it's not working. Any ideas why a display would tile like that?

---

### Post by yaroto98 on 2009-06-04
After some hardware specific google-ing I learned that the HP/Nvidia combo with my card is a known overheating problem where the card dies (generally right after warentee). My next laptop won't be an HP

---

