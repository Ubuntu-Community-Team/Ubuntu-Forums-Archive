---
title: "Laptop video setup"
date: 2011-02-18
forum: Hardware
---

### Post by novaris on 2011-02-18
I have just tried installing Ubuntu 10.041 on an old Acer Travelmate  740. It installed ok but has only 800x600 as the maximum resolution and  if I plug it into a projector there is no image on the projector and the  laptop image is corrupted.

I have searched the forums and google but I simply get overwhelmed with  hint's and suggestions that are getting me nowhere. So hopefully someone  can suggest a process to trouble shoot and resolve the problem.

---

### Post by SnickerSnack on 2011-02-18
What is the native resolution on the laptop's display?

I recommend you learn a bit about xrandr.  I use xrandr to handle all my external and primary video needs.

Here is a post where I give some info on xrandr): [http://ubuntuforums.org/showpost.php?p=10306942&postcount=2](http://ubuntuforums.org/showpost.php?p=10306942&postcount=2)

Please feel free to ask more specific questions.

Also, I suspect that you will need to edit an xorg config file and add the higher resolutions you need, though it has been quite a while since I've dealt with that, and so I can't help you with that.

Run

```

xrandr --prop

```

from the terminal and show us the output.

---

### Post by novaris on 2011-02-19
ok here is the output from xrandr --prop
```
Screen 0: minimum 320 x 200, current 640 x 480, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
    load detection: 1 (0x00000001)    range:  (0,1)
LVDS connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
    scaling mode:    Full
        supported: None         Full         Center       Full aspect 
   1400x1050      60.5 +   60.0  
   1600x1024      60.2  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9*    59.4  
S-video connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
    tv standard:    ntsc
        supported: ntsc         pal          pal-m        pal-60      
                   ntsc-j       scart-pal    pal-cn       secam       
    load detection: 1 (0x00000001)    range:  (0,1)
   800x600        59.9 +
   640x480        59.9* 

```I dont have any TV output so I don't know why that is showing.

---

### Post by novaris on 2011-02-27
Ok forget it!

I have been struggling with this for over a week with no results and limited help. I had been led to believe Linux was good and easy to setup. Yeah Right. Oh well back to windows it is.

---

