---
title: "No power management was installed"
date: 2004-11-08
forum: Hardware &amp; Laptops
---

### Post by duff on 2004-11-08
Hi all -

After testing out Ubuntu on a spare desktop and laptop and liking it, I finally decided to install it on my main laptop where I do all my work.  Unfortunatly, neither ACPI or APM was installed, so I don't get battery status, temperature readings, and it doesn't turn off automatically (I have to hit the power button -- how archaic :p).  I've been running Gentoo on this laptop for over 2 years, so I know it works, and the first laptop I installed Ubuntu on installed ACPI correctly. It even automatiically adds the battery status and wireless netwokring applets in GNOME (great!).  I tried running "sudo laptop-detect", but nothing happened .. nothing was even printed to the terminal.

So what's up?  Is there a way to tell the OS that "yes you can do ACPI!", without building a custom kernel.

Thanks.

---

### Post by duff on 2004-11-09
Hmmm..well I think I found out why.  "laptop-detect" uses dmidecode to figure out if the system is a laptop or not, and mine says this:
```
Chassis Information
                Manufacturer: No Enclosure
                Type: Other
                Lock: Not Present
                Version: N/A
                Serial Number: None
                Asset Tag: No Asset Tag
                Boot-up State: Safe
                Power Supply State: Safe
                Thermal State: Safe
                Security Status: None
                OEM Information: 0x00001234
``` 
 :?  Not much information there, espically the important Type field.  Is there a way I can force all the available laptop features to get installed and set up.  I'm supposing there's a script somewhere that just says ```
/usr/sbin/laptop-detect && do_laptop_stuff
```I just can't seem to find it.  Anybody got any pointers?

Thanks.

---

### Post by Johan on 2004-11-13
[QUOTE=duff]```
/usr/sbin/laptop-detect && do_laptop_stuff
```I just can't seem to find it.  Anybody got any pointers?
[/QUOTE]

Try using ```
/etc/init.d/laptop-mode start
``` and see if that helps.

---

