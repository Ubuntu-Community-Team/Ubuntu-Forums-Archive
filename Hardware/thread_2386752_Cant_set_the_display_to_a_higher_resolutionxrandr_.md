---
title: "Cant set the display to a higher resolution/xrandr: Failed to get size of gamma for o"
date: 2018-03-09
forum: Hardware
---

### Post by eflix1 on 2018-03-09
Hello! Im having a problem with the resolution of my screen after an update. 
When I boot normally the screen goes black (As if the computer was turned off). If I boot in recovery mode I can get to see the desktop environment, although with lower resolution (1024x768) and an error message pops up that says "xrandr: Failed to get size of gamma for output default" 


```
xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1280 x 1024
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      61.00* 
   800x600       61.00  
   640x480       60.00  
   1280x1024_60.00  59.89  

```



```
xrandr  -s 1280x1024_60.0  
Failed to change the screen configuration!

```

I tried to install the proprietary AMD driver but It doesnt work. I also tried to add an xorg.confi file to /etc/X11 that I found in another forum, and all I got was a black screen with a blinking prompt.
I have tried several solutions available online but none of them have worked. For now all I could get is to increase the maximum resolution available when I type xrandr.
My computer is running Ubuntu 18.04 Bionic Beaver.
Thanks in advance!.

---

