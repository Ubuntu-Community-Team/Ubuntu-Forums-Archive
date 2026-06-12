---
title: "Battery won't charge under Ubuntu"
date: 2013-07-31
forum: Hardware
---

### Post by EddyTheB on 2013-07-31
I have a new Asus Q550L ([https://www.asus.com/supportonly/Q550LF/](https://www.asus.com/supportonly/Q550LF/)). I removed Windows 8 and replaced it with Ubuntu 13.04, and now the battery won't charge. If it's plugged in then it sits at a constant battery level (currently 65%), if unplugged it slowly drains. Either way the orange battery light flashes on the front, which is supposed to indicate that the battery has less than 10% charge and is charging. There are some things that suggest that the problem is with Ubuntu, and some that suggest the problem is a circuitry problem.

If I turn the laptop off and leave it plugged in the orange light continues to flash, when I turn the computer back on again it will not have charged anywhere beyond where it was. (Turned off and unplugged, the light stays off). This suggests that the problem is with circuitry right?

However, if I boot from the windows repair disk then the laptop charges, that is currently my only way of charging the laptop.

Is there some Ubuntu battery driver software that could be malfunctioning? Even when the laptop is turned off? The only other explanation I can think of is that perhaps the connection comes in and out and it is a bizzare coincidence that it works when the windows disk is in.

I can't reinstall windows, it won't allow me to restore from the system image I saved. That's something I'll have to figure out if we decide the problem is a hardware problem, I have about 5 days left in which I can return the laptop to the store, but first I'll need to return it to windows. But that's a whole other problem.

---

### Post by slw210 on 2013-07-31
Seems odd that it doesn't charge when powered off.

Have you checked settings in the BIOS?

---

### Post by EddyTheB on 2013-07-31
I have, but I haven't seen anything related to the battery. What sort of thing would I be looking for? In order to boot Ubuntu I currently need to have "Fast Boot" and "Secure Boot" disabled, "Launch CSM" enabled, and to boot from "P0: ST1000LM024 HN-M101MBB".

---

### Post by slw210 on 2013-07-31
Try another distro or 12.04 LTS from a Live CD and see if it charges.

Still seems odd it doesn't charge when turned off, sounds like something is tied in to needing Windows installed to charge. 

I would call Asus and see what's going on or reload Windows and return it.

---

### Post by EddyTheB on 2013-07-31
Tried 12.04 LTS, still no charging. But I also retried the windows repair dvd, and it will no longer charge when booted from that either. It definitely did charge last time I tried that but I suppose that was just lady luck throwing me something to confuse me.

Now I just need to reinstall windows so that I can return the laptop.

Thanks for your advice.

---

### Post by lah7 on 2013-07-31
Is the battery removable from the system? Try taking it out, plugging into AC only and seeing how it behaves. You might be able to plug in the battery whilst it's on AC power to see if it charges or just sits there.

When you get Windows 8 back on the laptop, or if you remember... is there any utility that came with the system that modified the battery behaviour? But this is indeed a really strange case.

---

