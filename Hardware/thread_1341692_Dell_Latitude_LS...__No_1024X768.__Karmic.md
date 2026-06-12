---
title: "Dell Latitude LS...  No 1024X768.  Karmic"
date: 2009-11-30
forum: Hardware
---

### Post by Nylo on 2009-11-30
Every time there is an update I loose something. This time its my 1024X768 res.  Ive searched these forums with no luck.  With no way to edit (Xorg.conf) Im not sure what to do.

Tale Of The Tape.............

**ubuntu007@ubuntu:~$ lspci**

01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)

** ubuntu007@ubuntu:~$ xrandr -q**


Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600

default connected 800x600+0+0 0mm x 0mm

   800x600        60.0*    56.0  

   640x480        60.0  

   320x240        60.0

**ubuntu007@ubuntu:~$ sudo lshw -c display**

  *-display UNCLAIMED     

       description: VGA compatible controller

       product: NM2200 [MagicGraph 256AV]

       vendor: Neomagic Corporation

       physical id: 0

       bus info: pci@0000:01:00.0

       version: 20

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list

       configuration: latency=128 maxlatency=255 mingnt=16

       resources: memory:f6000000-f6ffffff(prefetchable) memory:fe400000-fe7fffff memory:feb00000-febfffff

---

