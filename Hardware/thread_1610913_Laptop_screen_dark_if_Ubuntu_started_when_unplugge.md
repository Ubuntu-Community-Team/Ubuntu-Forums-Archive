---
title: "Laptop screen dark if Ubuntu started when unplugged"
date: 2010-11-01
forum: Hardware
---

### Post by Sidrabs on 2010-11-01
Hello,

I hope this can be solved by some easy fix...

So, the problem is, that when I start up my power-unplugged laptop with Ubuntu (64bit, ver. 10.10), the screen is very dark. Operating the Fn+ buttons to change the brightness does not help, although I can see on the screen the pictogram of "sun" and changing progress bar. Those very buttons operate fine, when laptop is started with power cord plugged-in.

The laptop model is Dell Vostro 3300.

---

### Post by Wobblybob on 2010-11-01
Not on lappy at the mo or Ubuntu but try [System], [Preferences], [Power Management]. You'll then see tabs for On AC Power and On Battery Power if I remember and you can pick the setting you want to adjust, I'm sure I set mine to never dim.

---

### Post by Sidrabs on 2010-11-06
I'm not sure what happened then, but without me doing any adjustments to settings, Ubuntu now starts up normal when in battery mode.

The only abnormality is when I run it with power cable attached, and then pull it out, Ubuntu warns that battery is at extremely low level and proposes to hibernate immediately. Though the battery is fine. I guess when the laptop switches from power to battery mode,  there is some minisculous moment while it reports to the OS low battery level?

---

### Post by P4man on 2010-11-06
start 

```
gconf-editor
```

Browse to this key:

/apps/gnome-power-manager/general/use_time_for_policy

And change its setting.

Alternatively, experiment with acpi_osi settings, see the link in my signature.

---

