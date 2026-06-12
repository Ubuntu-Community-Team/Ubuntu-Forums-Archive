---
title: "Samsung Monitor Problem"
date: 2011-05-25
forum: Hardware
---

### Post by dacoconuttman on 2011-05-25
Hello
I bought a new Samsung monitor because my old one broke. During the transition, I used a backup NEC monitor. Instead of displaying at 1080p, the computer detects max resolution as 1024x768. Why is tis happening, and how can I fix it? The computer is running Natty x64 with an Nvidia graphics card.

---

### Post by krapp on 2011-05-25
This isn't a monitor problem but a driver problem, and it may not be a problem at all. It would be helpful if you could post here the output of

```
xrandr
```

---

### Post by papibe on 2011-05-25
Do you have or use an X config file? (/etc/X11/xorg.conf)

If you do, try to remove it (actually just rename it):
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
then, reboot and try to set the resolution again.

Hope it helps.

---

### Post by dacoconuttman on 2011-05-25
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1920 x 1080
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0     51.0     52.0     53.0     72.0     73.0* 
   832x624        54.0  
   800x600        55.0     56.0     57.0     58.0  
   720x450        59.0  
   680x384        60.0     61.0  
   640x480        62.0     63.0     64.0     65.0     66.0  
   512x384        67.0     68.0  
   400x300        69.0  
   320x240        70.0     71.0  
   1360x768       72.0  
   1920x1080      73.0     72.0  

```
Its an LCD monitor, so the refresh ts too high for the hi-res. I already messed around with the resolution file to add the 1080p, but it gave me this and it doesn't work.

---

### Post by krapp on 2011-05-25
Have you had a look here [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) for how to add new modes to randr?

---

