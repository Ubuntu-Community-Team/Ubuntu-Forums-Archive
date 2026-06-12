---
title: "LG IPS235V-BN and Nvidia non free"
date: 2013-03-27
forum: Hardware
---

### Post by probu on 2013-03-27
Since I've got this 23" screen I was never able to install the original Nvidia driver. It allways returns a blank screen. No matter what the distro is, the DE environment... nothing.

The main hint is that dysplay managers allways see this monitor as if it were 2 screens. 

Exemple: Xubuntu 12.04.2

Output 1 - "Digital dysplay", max res 840x480. 

Output 2 - "LG Electronics 23", max res 1920x1080.

Does this ever happened to some of you?



xrandr -q

```
manxub@965P-DQ6:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
DVI-I-1 connected 848x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   848x480        60.0* 
   640x480        59.9  
DVI-I-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
TV-1 disconnected (normal left inverted right x axis y axis)
manxub@965P-DQ6:~$ 


```

---

