---
title: "800 x 600 max resolution after new install"
date: 2010-07-13
forum: Hardware
---

### Post by Pete051 on 2010-07-13
Hi people
just installed LTS version of Kubuntu on my dual boot Novatech laptop and the maximum resolution I can get is 800 X 600.
Using xrandr tells me

peter@one:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

and lspci tell me

[...]
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

and I can see no way to get a more useful resolution, ideas anyone?
Thanks
Pete

---

### Post by IcarusR on 2010-07-13
Probably lack of driver.

Checkout the first post on this page...

[http://wiki.ubuntuforums.org/showthread.php?t=958967&page=38]("http://wiki.ubuntuforums.org/showthread.php?t=958967&page=38")

---

