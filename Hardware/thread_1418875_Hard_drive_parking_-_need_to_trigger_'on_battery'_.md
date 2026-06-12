---
title: "Hard drive parking - need to trigger 'on battery' behavior"
date: 2010-03-01
forum: Hardware
---

### Post by chris billington on 2010-03-01
I've almost got my acer extensa 5620 to stop parking its hard drive constantly under Ubuntu 9.10. (the infamous [bug #59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695"))

With my current configuration settings the hard drive parking appears to be only occurring after the idle times I've set in gconf-editor > apps > gnome-power-manager > disks. This is very good.

I dont have a problem on AC power, and when I unplug power that idle time kicks in as desired. However if I BOOT whilst on battery, the disk parks every 10 seconds or so!

There must be some command that gets executed when the laptop goes from AC to battery power - if so, does anyone know what it is, so I can schedule it to happen at login?

---

### Post by chris billington on 2010-03-01
Ok I found a solution. The required command was:

```
hdparm -B 254 /dev/sda
```

which sets the  Advanced Power Management setting of my drive to '254'. I don't know what 254 means, but I know that thats what the setting is when things are working (after removing AC power)

But hdparm needs to be run as a superuser, so instead of adding it to startup programs, I added it to /etc/rc.local.

---

