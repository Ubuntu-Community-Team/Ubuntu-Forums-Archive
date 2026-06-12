---
title: "Peculiar Problem With Brightness on Intrepid"
date: 2009-02-04
forum: Hardware
---

### Post by sourasteroid on 2009-02-04
Having read countless threads on fixing the brightness problem I followed the workaround using lcdbryt.sh and editing
 /etc/acpi/video_brightnessup.sh and *down.sh.

The small script works by reading values from /proc/acpi/video/VGA/LCD/brightness

Before a recent update (linux headers for 2.6.27) i was able to change my brightness either using my buttons or by directly changing the value in /proc/acpi/video/VGA/LCD/brightness

using echo -n [some fixed value] > /proc/acpi/video/VGA/LCD/brightness

But all of a sudden my /proc/acpi/video/VGA folder is gone! Now I have a GFX0 folder with a variety of "displays" like DD01 DD02 etc. 

I've tried changing the values of the brightness in each of these but to no avail. The only thing that works is booting to an older version using the grubloader at boot.

Does anyone know how i can get my /proc/acpi/video/VGA folder and contents back?

Thanks for reading this long post :D

---

### Post by Mlok on 2009-02-06
I'll be following this thread - I am interested in anything about brightness control : I have never been able to control it on my laptop (since ubuntu 6.10 I think)

---

