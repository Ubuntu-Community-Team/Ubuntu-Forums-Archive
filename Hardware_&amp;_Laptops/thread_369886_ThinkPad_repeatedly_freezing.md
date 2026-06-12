---
title: "ThinkPad repeatedly freezing"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by trevorv on 2007-02-25
Hiya,

Recently, my ThinkPad R50e (Running Edgy) has begun to freeze, totally and utterly, so that the only thing one can do is cut off it's power. I'm assuming this is a hardware issue as there doesn't seem to be any continuity between crashes. They appear to be random (the only action which always results in freezing is opening F-Spot, or browsing my photos in Nautilus -- a problem with the hard drive where these are stored perhaps?) and can sometimes even trigger before GNOME is entirely finished booting.

To be honest I don't really have any idea how to figure out what's going wrong, and would appreciate some help in figuring out what the problem is.

Thanks :)

---

### Post by vyruss on 2007-03-09
> **trevorv said:**
> Hiya,

Recently, my ThinkPad R50e (Running Edgy) has begun to freeze, totally and utterly, so that the only thing one can do is cut off it's power. I'm assuming this is a hardware issue as there doesn't seem to be any continuity between crashes. They appear to be random (the only action which always results in freezing is opening F-Spot, or browsing my photos in Nautilus -- a problem with the hard drive where these are stored perhaps?) and can sometimes even trigger before GNOME is entirely finished booting.

To be honest I don't really have any idea how to figure out what's going wrong, and would appreciate some help in figuring out what the problem is.

Hi, please try this: ```
sudo gedit /boot/grub/menu.lst
```Find the section that starts with:```
title		Ubuntu, kernel 2.6.17-11-generic
```and at the line that says:```

kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=7c0afac4-2373-48ef-9a7e-c4cb2355cf0c ro quiet splash
``` add ***noapic nolapic*** after *quiet splash* so that it reads:```
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=7c0afac4-2373-48ef-9a7e-c4cb2355cf0c ro quiet splash noapic nolapic
```

Then save the file and reboot. This killed the random freezes on my laptop. Just remember to restore the words*** noapic nolapic*** after a kernel update, because they'll get erased.

---

### Post by trevorv on 2007-03-10
Thanks for the reply :)

I've sinced ditched GNOME entirely, am currently using Fluxbox (with hardly any graphical apps) and plan to move on to Rat Poison soon. I haven't experienced any problems since the switch.

If I do experience issues again, however, I'll keep your advice in mind thanks :)

---

