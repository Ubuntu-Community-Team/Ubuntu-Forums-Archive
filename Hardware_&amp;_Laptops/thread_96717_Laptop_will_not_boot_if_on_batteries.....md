---
title: "Laptop will not boot if on batteries...."
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by jakev383 on 2005-11-29
I made comment of this in another thread, but here's my situation:
Dell Inspiron 600m laptop. Working great after tweaking. Boots fine when plugged in, hibernation works, wireless works via driverloader, yada yada yada.  When I'm on batteries, boot up hangs when it's starting PCMCIA services (right after ALSA 0). Hangs hard.  Have to hard-reboot it to get it to come back. I can keep doing this all day long, but it hangs in the same spot (it used to boot fine after the 3rd or 4th try when I was running the devel version of Breezy).  *If I plug it into power*, it will boot fine. Hibernation works fine either way. I usually leave my power supply at the office (between wife, dog, home-built CNC projects, MythTV project, QMail, etc. I never run the battery down at home), and every once in a while hibernation hangs (about 1 out of every 40 hibernations) so I have to hard-boot the machine.  Since the power supply is not handy, I end up not being able to use the laptop until the next day when I get to work and plug it back in so it can boot normally.  It only does this when it's on batteries.  I'd assume it's something to do with ACPI, and maybe the BIOS not firing up PCMCIA on batteries unless it's needed, but poke me if I knew where to start looking.
Anyone else have any similar problems, or know of a fix?
Thanks in advance.

---

### Post by wrtrdood on 2005-11-29
It does sound as if it may be a power-saving BIOS feature getting in the way.  That or a Plug-n-Play problem.  The latter one can be an issue with laptops.  If you can change the PnP options, check this and make sure it's off.  I know some hardware has a real trial with this sort of thing.  

This is a tough one since there won't be much logging support that you can check.  One possibility is to ALT F1 through F4 and check the screens there.  I don't recall exactly but I know at least one of those terminal screens should have a log you can check.

---

### Post by jakev383 on 2005-11-29
[QUOTE=wrtrdood]It does sound as if it may be a power-saving BIOS feature getting in the way.  That or a Plug-n-Play problem.  The latter one can be an issue with laptops.  If you can change the PnP options, check this and make sure it's off.  I know some hardware has a real trial with this sort of thing.  

This is a tough one since there won't be much logging support that you can check.  One possibility is to ALT F1 through F4 and check the screens there.  I don't recall exactly but I know at least one of those terminal screens should have a log you can check.[/QUOTE]

I went into the BIOS to turn off the PNP functions, but it doesn't have any.  I looked around a little more, and the only thing that even looked remotely close (besides hot/warm swapping for a docking station) had to do with USB functions for keyboards/mice for OS's that normally don't support them. I turned this OFF and guess what! I just rebooted the thing twice on batteries to make sure it was working. I don't know what this would have to do with it being plugged in or on batteries, but I'm not going to look a gift horse in the mouth.
Thanks for the tip!

---

### Post by ubunny on 2005-11-30
how about laptop-mode script or something like that in the /etc/defaults area?  This dims the screen and generally puts the system in a state that runs better while on the battery.  Too dim for me though, so I don't use it.

hth

---

### Post by jakev383 on 2005-11-30
[QUOTE=ubunny]how about laptop-mode script or something like that in the /etc/defaults area?  This dims the screen and generally puts the system in a state that runs better while on the battery.  Too dim for me though, so I don't use it.[/QUOTE]

I'm lucky enough that on my Dell Inspiron 600m the brightness gets controlled via the BIOS, so the Fn-DIM keys worked for me out of the blocks.
I looked at the laptop-mode config file in /etc/default, as well as a few others in there, but I'd need to know what they do exactly before I started monkeying with them.  
I have not had a problem since I changed that USB keyboard setting, though. I didn't have any PNP stuf in the BIOS, so that was the closest thing I could find to change.

---

