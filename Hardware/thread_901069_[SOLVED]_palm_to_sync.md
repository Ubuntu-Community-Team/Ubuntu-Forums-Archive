---
title: "[SOLVED] palm to sync"
date: 2008-08-26
forum: Hardware
---

### Post by GrnFrag on 2008-08-26
Hi again all.   I've been trying to get my palm to sync and not having much luck.    So in my travels i found this page
[HTML]http://ubuntuforums.org/showthread.php?t=533116&highlight=m130[/HTML]
And did this 8-[
```

gksudo mknod /dev/ttyUSB0 c 188 0 # found these statements on other forum
gksudo mknod /dev/ttyUSB1 c 188 0 # found these statements on other forum
gksudo mknod /dev/pilot c 188 0 # added this statement based on above info
gksudo chmod 666 /dev/pilot # added this statement based on above info

```
it didn't help, and from my other research i think i've blocked the usb ports with this.     How would i remove these (portmappings? is that the right name)

Thanks again

---

### Post by chrisdeckard on 2008-08-26
Just use rm.  Devices are just files in Linux.

-Chris

---

### Post by GrnFrag on 2008-08-26
got those devices removed, Still no love on the palm :(    When i try to load visor, in my /var/log/messages i see
```
Aug 26 08:59:17 MoonRock kernel: [ 1013.419686] visor: probe of 2-1:1.0 failed with error -5
```
at this point i'm not loading visor upon reboot, it's being loaded manually.  i have specified the device id's for the palm to visor. when i hit the hotsync, i can see it when i run lsusb (that's where i got the device id's) 
i'm stumped.   anyone have any info on this error
i forgot to mention that i have read the posts on how to setup your palm with Ubuntu.   I followed the directions, but nothing works.

---

