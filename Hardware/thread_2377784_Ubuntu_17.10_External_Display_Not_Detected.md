---
title: "Ubuntu 17.10 External Display Not Detected"
date: 2017-11-16
forum: Hardware
---

### Post by cowpicket on 2017-11-16
I have been trying to solve this problem for a few months now. I have an external monitor that I have been using for some time and for some reason has stopped working with my Ubuntu machine. 

I posted before in an earlier thread but got no replies ([https://ubuntuforums.org/showthread.php?t=2371551](https://ubuntuforums.org/showthread.php?t=2371551)). 

I recently re-imaged my PC with Ubuntu 17.10 in the hopes it would clear any issues preventing the previous installation from malfunctioning, but to no avail. 


Could really use some help. Thanks in advance. 

```

uname -ar

Linux 4.13.0-16-generic #19-Ubuntu SMP Wed Oct 11 18:35:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```


```

lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5300 (rev 09)

```


```

xrandr -q

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
XWAYLAND0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 290mm x 170mm
   1920x1080     59.96*+

```

---

