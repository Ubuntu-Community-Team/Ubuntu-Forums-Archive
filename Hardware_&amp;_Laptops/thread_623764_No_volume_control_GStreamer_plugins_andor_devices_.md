---
title: "No volume control GStreamer plugins and/or devices found"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by nnamdi on 2007-11-26
there is a red x sign on my speaker
i have installed the alsa ver 5 for drive,lib and utils
then i saw the red x sign before i did that there was no sign like but i did not have sound either.

i use a hp pavilion dv 6000 serise
when i run:
pradeep@pradeep-laptop:~$ sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
pradeep@pradeep-laptop:~$

---

### Post by nnamdi on 2007-11-26
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
so i wen to this site

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by daine33 on 2007-12-10
I've been looking all over for this. This got my audio working again :) Thanks!

---

