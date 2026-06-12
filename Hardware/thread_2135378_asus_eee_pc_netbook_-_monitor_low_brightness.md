---
title: "asus eee pc netbook - monitor low brightness"
date: 2013-04-14
forum: Hardware
---

### Post by sbarzucco on 2013-04-14
Hi all

i installed on my netbook  lubuntu but the brightness of my monitor is low :-(

Before to install lubuntu i had ubuntu in the same laptop without issues 

I tried to improve brightness with this command (after i tried with keyboards and  monitor settings etc)

[COLOR=#555555][FONT=Monaco]gksu leafpad /sys/class/backlight/acpi_video0/brightness

but it didn't work ...max value is 10 and it doesn't solve my issue

Any other way to help me?


Thanks in advance[/FONT][/COLOR]

---

### Post by TheFu on 2013-04-14
I have an Eee too.  Fn-F6 and Fn-F5 control the monitor brightness in hardware.

---

### Post by sbarzucco on 2013-04-14
> **TheFu said:**
> I have an Eee too.  Fn-F6 and Fn-F5 control the monitor brightness in hardware.


I did it for first ....it's a monitor driver issue 

where can i find right drivers for lubuntu?

---

### Post by TheFu on 2013-04-14
> **sbarzucco said:**
> I did it for first ....it's a monitor driver issue 

where can i find right drivers for lubuntu?

I'm running 12.04 with Ubuntu Server and LXDE added on top. This is a stripped down Lubuntu ... less bloat, IMHO. Monitor brightness works flawlessly with the automatic drivers from the repo.  If you have specialized driver needs, then you'll need to know the specific chips involved.  For monitors, the most that I've needed to change was the resolution after seeing which resolutions were available. xrandr is that command.  Almost always when I needed to do more with monitors, it was addressed in the /etc/X11/xorg.conf file.  Always make a backup before every change, then restart X/Windows to see your changes. Capabilities for every monitor would be provided from the monitor manufacturer.  There is no driver for a monitor, just specific X/Windows settings.  At least that's the way it has always worked.  I've never heard of the .config/monitor* file you mention, so I could be behind the times?

---

