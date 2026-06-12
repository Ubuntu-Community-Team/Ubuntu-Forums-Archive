---
title: "Quadro FX 2700M cannot select 1680x1050"
date: 2009-10-04
forum: Hardware
---

### Post by graysky on 2009-10-04
Using v185.18.36 nvidia driver on a notebook PC that uses the Quadro FX 2700M.  I can't select 1680x1050 (it's not in the list) from the nvidia-settings.  It drops from 1920x1200 to 1400x1050!  If I boot the PC into Windows XP I can select 1680x1050 no problem.  Here is what xrandr says:

```
$ xrandr
Screen 0: minimum 320 x 240, current 1920 x 1200, maximum 1920 x 1200
default connected 1920x1200+0+0 0mm x 0mm
   1920x1200      50.0* 
   1400x1050      51.0  
   1280x1024      52.0  
   1280x960       53.0  
   1024x768       54.0  
   800x600        55.0     56.0  
   700x525        57.0  
   640x512        58.0  
   640x480        59.0     60.0  
   512x384        61.0  
   400x300        62.0  
   320x240        63.0
```

Any ideas how I can run in 1680x1050?

---

