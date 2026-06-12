---
title: "Monitors not detected in 11.04"
date: 2011-05-03
forum: Hardware
---

### Post by cbob on 2011-05-03
Hi,
Just upgraded to 11.04 but after the upgrade no monitor is any longer detected..
Not the internal(I'm using a netbook) or the external(when ever one is connected).

Some data..
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

```
```
$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 600, current 1024 x 600, maximum 1024 x 600
default connected 1024x600+0+0 0mm x 0mm
   1024x600        0.0* 
```
Any thought?

Regards
cbob

---

