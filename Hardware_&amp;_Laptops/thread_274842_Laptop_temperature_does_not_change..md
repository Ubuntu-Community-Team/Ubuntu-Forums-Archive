---
title: "Laptop temperature does not change."
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by the_0ne on 2006-10-10
I found a thread on the ubuntuforums on how to monitor your laptop temperature.  I found these 2 methods...

```
acpi -V
```

... and ...

```
cat /proc/acpi/thermal_zone/THRM/temperature
```

I get this from acpi -V...

```

Battery 1: charged, 100%
Thermal 1: ok, 75.0 degrees C
AC Adapter 1: on-line

```

and this from cat'ing temperature...

```

temperature:             75 C

```

It never changes.  It's always 75.0 C.  Does that make sense?  I've tried running a cpu intensive script and still no change.  Are there other ways to monitor the temperature of  my laptop?

---

### Post by IcemanV9 on 2006-10-10
Methods that you mentioned are perfect. That's what I use for my two laptops.

However, I use an excellent temp monitor **[COLOR="Orange"][applet]("http://computertemp.berlios.de/")[/COLOR]** for one of mine since it gets so **[COLOR="Red"]HOT[/COLOR]** easily. 72C (65C idle) will shut it down gracefully. :(

---

### Post by the_0ne on 2006-10-10
> **IcemanV9 said:**
> However, I use an excellent temp monitor **[COLOR="Orange"][applet]("http://computertemp.berlios.de/")[/COLOR]** for one of mine since it gets so **[COLOR="Red"]HOT[/COLOR]** easily. 72C (65C idle) will shut it down gracefully. :(

Thanks, I'll check that one out when I get home from work.

---

### Post by NeoLithium on 2006-10-10
Allright, thank you SO much for this post; It'll help me fix up some gdesklet applets that never registered my temperature before!  Just never had luck figuring out where to get it to pull the data.

:)

---

### Post by the_0ne on 2006-10-10
> **IcemanV9 said:**
> Methods that you mentioned are perfect. That's what I use for my two laptops.

However, I use an excellent temp monitor **[COLOR="Orange"][applet]("http://computertemp.berlios.de/")[/COLOR]** for one of mine since it gets so **[COLOR="Red"]HOT[/COLOR]** easily. 72C (65C idle) will shut it down gracefully. :(

Strange, I downloaded the applet, installed it and added it to my gnome panel.  Still my temperature always stays at 75 celsius.  :(  Has anybody else had this problem?  Is there something I must do to monitor my laptop temperature that might not be running?

---

### Post by Angafirith on 2006-10-10
I have the same problem on both of mine. My laptop always says 0 degrees Celsius, no matter what. My desktop here always says 40 degrees Celsius. My old server would always fluctuate between -80 and -81 or so.

Out of curiosity, is your machine an amd64?

---

### Post by the_0ne on 2006-10-10
> **Angafirith said:**
> Out of curiosity, is your machine an amd64?

nah, it's an Intel 3.0 ghz.

---

