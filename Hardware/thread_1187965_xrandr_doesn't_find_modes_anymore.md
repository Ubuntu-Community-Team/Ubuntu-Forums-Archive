---
title: "xrandr doesn't find modes anymore"
date: 2009-06-15
forum: Hardware
---

### Post by planetLars on 2009-06-15
Hello,

xrandr doesn't find the modes of my external display anymore. Last week everything worked fine. I use a laptop. I already experienced peculiar behaviour when a display I connected to over the weekend wasn't recognized anymore (an iiyama 510 pro crt) by ubuntus own display preference when it was 2 weeks ago. Now my Samsung tfts modes are not shown anymore. See [here]("http://ubuntuforums.org/showpost.php?p=7404056&postcount=5") for how it still looked like last week (also note a potential bug mentioned there I didn't report as such). Now it looks like this:
```
lars@lars-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2080 x 800
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1024x768       75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1 
```

Help appreciated!

Best and Kind Regards

Lars

---

### Post by planetLars on 2009-06-15
Didn't xrandr got updated last week? Anyway, it now exhibits the same bug for me Ubuntus display preference does for me: higher res are not available when the systems boots with a lower res.

I used cvt to create a modeline for my resolution and then add a --newmode to xrandr with the appropriate resolution.

Check with your (online) display manual that the pixel clock delivered is supported by the display for the given Vesa resolution.

After adding and applying the newmode (at first xrandr didn't want to apply as it found a wrong max res but the display preferences then offered the high res via which it all worked) xrandr showed all less res modes correctly.

---

