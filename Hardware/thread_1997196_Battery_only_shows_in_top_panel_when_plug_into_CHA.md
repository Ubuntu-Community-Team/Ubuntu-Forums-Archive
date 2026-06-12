---
title: "Battery only shows in top panel when plug into CHARGER"
date: 2012-06-04
forum: Hardware
---

### Post by abimael08 on 2012-06-04
Never shows on startup, only shows when i plug in charger and/or only shows when there is about 10% left. Is there anyway to fix this issue?

Ubuntu 12.04
Toshiba Satellite L745-S4310
BIOS is UPDATED


[IMG]http://25.media.tumblr.com/tumblr_m54eyudQDc1rxi2c0o1_1280.png[/IMG]

---

### Post by typhoon_tip on 2012-06-04
Have you checked the battery preferences in the Power Settings ? Just open System Settings/Power Settings. Mine is set to show battery "**When battery is present**".

---

### Post by abimael08 on 2012-06-04
Yes i Set it to show when battery is present and charging but it never shows and the option changes back to blank as if i didnt set it, after exiting and coming back to it

---

### Post by sammiev on 2012-06-04
Hope this helps you.

---

### Post by typhoon_tip on 2012-06-04
> **abimael08 said:**
> Yes i Set it to show when battery is present and charging but it never shows and the option changes back to blank as if i didnt set it, after exiting and coming back to it

```
simone@simone-ThinkPad-T400:~$ sudo acpi -b
Battery 0: Unknown, 99%
simone@simone-ThinkPad-T400:~$ dmesg | grep batt
[    0.668549] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.668557] ACPI: Battery Slot [BAT0] (battery present)
[    0.681994] ACPI: Battery Slot [BAT0] (battery present)

```

I checked my output compared to yours above, the line "Firmware Bug" is not nice... I think something is wrong in either your ACPI or a bug in the Linux Firmware Kernel.

If you have the possibility (and you are comfortable with it, absolutely **do _not_ do it** if you are not 100% confident !!) try a BIOS upgrade of your laptop, it may correct the battery rate reporting issue.

If not, you can report a bug in Launchpad.

---

### Post by abimael08 on 2012-06-04
I think its Linux Kernel, because I have an updated BIOS, just released MARCH 2012

---

### Post by abimael08 on 2012-06-04
did that and it doesnt work, ill reboot my computer and attach an image so you can see, ill check that option to show when charging and present but it will not show up and ill receive the same results

---

### Post by abimael08 on 2012-06-04
I rebooted and got same result. ANY SUGGESTIONS?

[IMG]http://25.media.tumblr.com/tumblr_m54g98mNl11rxi2c0o1_1280.png[/IMG]


[IMG]http://25.media.tumblr.com/tumblr_m54gf73qtk1rxi2c0o1_1280.png[/IMG]

---

### Post by typhoon_tip on 2012-06-04
Just noticed "Battery absent" label above...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703302](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/703302)

Check this, see if it fits with all your symptoms.

---

### Post by typhoon_tip on 2012-06-04
Weird, a fix was released but seems you still got the bug... are you sure you are using 12.04 release and not beta 2 ??

---

### Post by abimael08 on 2012-06-04
i downloaded directly from ubuntu.com


[B][I][U]
UPDATE[/U][/I][/B]

I think i figured it out, Im updating the Kernel, still had 3.2 Kernel, Thanks for the support guys

---

