---
title: "Volume and brightness steps per click"
date: 2010-01-18
forum: Hardware
---

### Post by shaka_zulu on 2010-01-18
Hello there

I have a question about the thing i mentioned in the title. I have the following problem. On my laptop when i hit key combinations for brightness is is going up/down like 29% per click which is too much. The same thig is happening for volume but change is about 11%. I need to how i can reduce it so when i click key combination it goes up/down for 5%. 

Do you have any idea?

I have Dell XPS 1530, Core2Duo 2,5GHz, 4Gb RAM, nVidia M8600GT...

---

### Post by Zorael on 2010-01-18
Regarding brightness, this is usually a hardware/bios/driver limitation. An example from my netbook;
```
$ **cat /proc/acpi/video/IGD/LCD/brightness**
levels:  20 30 40 50 60 70 80 90 100
current: 20
```
I have nine levels of brightness. Even though KDE has a brightness slider that I can freely drag, it's obvious it's doing a step for each 10% (over 20%). Perhaps yours is like that, but to a greater extent.

Regarding sound, I'm not sure this can be easily configured.

---

### Post by shaka_zulu on 2010-01-19
> **Zorael said:**
> Regarding brightness, this is usually a hardware/bios/driver limitation. An example from my netbook;
```
$ **cat /proc/acpi/video/IGD/LCD/brightness**
levels:  20 30 40 50 60 70 80 90 100
current: 20
```
I have nine levels of brightness. Even though KDE has a brightness slider that I can freely drag, it's obvious it's doing a step for each 10% (over 20%). Perhaps yours is like that, but to a greater extent.

Regarding sound, I'm not sure this can be easily configured.


This command doesn't work here. Say' that there is no "such file or directory". 

Where is that slider for brightness? I am not sure that i have seen it before.

---

### Post by Zorael on 2010-01-19
Yes, supposedly the path varies depending on the make of the card. Mine is an Intel integrated graphics chipset.

You can reach the brightness slider either through a battery monitor widget, such as the one normally next to the clock in a default panel (on laptops), or via modifying your current power scheme in System Settings -> Advanced tab -> Power Management.

---

### Post by shaka_zulu on 2010-01-19
Ok. Thanks mate. Will help a bit. ;)

---

### Post by Yellow Pasque on 2010-01-20
I'm not sure about KDE, but in case a GNOME user sees this thread, GNOME stores the volume step setting in the gconf registry. Run gconf-editor and look under this key:
/apps/gnome_settings_daemon/volume_step

Maybe KDE has this option in kmix settings?

---

### Post by saygin on 2010-01-31
any solutions for volume thing yet?

---

