---
title: "acoustic management with hdparm"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-04-19
my laptop hd makes a lot of noise when spinning, and "clicks" every few seconds when idle. since i've observerd the exact same behaviour in windows before setting auto-acoustic management options with an Intel utility, i resorted to hdparm's -M option for setting acoustic management settings. 

however, hdparm will report that it's setting the option to whatever value i enter, but when i type "sudo hdparm -M /dev/hda" it will still report that the option is set to the default value, zero.

does this mean that my drive's acoustic management feature is unsupported by hdparm? doesn't hdparm normally respond with an error message when required to tweak an unsupported feature? do i have any other chance of setting acoustic management preferences in linux?

i'm using a 2.6 kernel, where acoustic management support should be present.

---

### Post by 23meg on 2005-04-19
i just noticed that the output i get from the -I parameter does show that the drive is using the mode that i issue with -M, which is "254 (fast)", even though -M itself still shows zero. however, when i explicitly set the mode to zero, -I won't show zero, but whatever the last issued mode was!

could this be a hdparm bug?

---

### Post by skoal on 2005-04-20
Yeah, seems like strange behaviour between -M/-I switches.  Whatever gremlins are scratching at code inside the hdparm binary, the -I reports the accurate acoustics (from my experience).  I just use -M to set the value.

The -I switch reports the setting accurately, right?

My drive reports a "recommended" acoustic setting and after changing it with -M it reports as such with -I.

---

