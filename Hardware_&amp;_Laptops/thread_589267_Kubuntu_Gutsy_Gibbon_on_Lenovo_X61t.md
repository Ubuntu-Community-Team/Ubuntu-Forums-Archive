---
title: "Kubuntu Gutsy Gibbon on Lenovo X61t"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by keith11 on 2007-10-24
Hello,

I have a question about the fan noise on Lenovo x61t. I am dual booting Kubuntu 7.10 with Vista Business 32-bit. My tablet machine was running fine very calmly and without any fan noise, even when powered. I am not sure if this is the reason but since I installed Kubuntu Gutsy Gibbon or near about that time, my fan is running constantly, irrespective of being on battery or plugged in and it happens in both Vista and Kubuntu. I can hear the sound of wind clearly in a library and it is so disappointing that it has started to act like this suddenly. Even with ambient noise, I can still hear the wind blowing. I have the following doubts regarding this whole situation:

1. Is it really the dual booting that is causing this?
2. Has installing Kubuntu Gutsy Gibbon put my fan on a constant speed where it just keeps running?
3. Is it the fan or the hard disk which makes that noise? I am confused about this because sometimes, I can't feel the wind blowing out of the vent as much but just the buzzing sound. Even in this case, all these noises are new as I never heard any such noise earlier.

Does anyone have a similar experience? I have tried searching for this issue and found a utility called tpfancontrol for Windows but I don't want to use anything that is not offered by lenovo/IBM itself, at least for the fan, as I think it is a critical component. Is there anything I can do in Vista or Kubuntu to solve this issue? Many thanks...

Keith.

---

### Post by keith11 on 2007-10-25
Any ideas anyone? Thanks.

Keith.

---

### Post by keith11 on 2007-11-01
Could someone throw some light on this issue, please? Thanks.

Keith.

---

### Post by isilmeraumo on 2007-11-21
I just got a new x61t and threw Ubuntu 7.10 on it and I have not experienced your issue.  I have read on a forums somewhere, I can't recall at the moment, that the problem you are experiencing was experienced by others as well.  My advice would be to contact Lenovo about getting it repaired as if it is occurring in both Ubuntu and Windows, it is probably a hardware issue.  Anyways, good luck.

---

### Post by essexboyracer on 2007-12-28
I am experiencing the same problem on my 7year old Tiny Laptop. I have tried various other distros in the past and win2k and this is the only time it has done this. It is the CPU fan running constantly. the laptop has a trident cyberblade ii gfx chip but i am pretty sure that doesnt have a fan associated with it on account of the laptop being so old. Nothing has changed in the BIOS, I ran xorg conf setup thingy and changed the gfx driver to vesa from trident, still no joy.

One thing I havnt tried yet is booting from the kubuntu 7.1 livecd to see if that does the same, though I am pretty sure it didnt I have seen somewhere on these boards about acpi, would adding the following to the grub menu.1st on the line that begins with the word kernel do anything to help?

```
acpi=off noacpi
```

---

