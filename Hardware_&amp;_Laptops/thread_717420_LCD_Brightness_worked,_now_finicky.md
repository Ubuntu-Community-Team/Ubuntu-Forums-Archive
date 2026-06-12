---
title: "LCD Brightness worked, now finicky"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by BandD on 2008-03-07
I had some difficulties getting Gnome Power Management to control my screen brightness on my Vaio FS620 when I first installed Gutsy.  You can see my thread here:
[URL="http://ubuntuforums.org/showthread.php?t=650566"]
http://ubuntuforums.org/showthread.php?t=650566[/URL]

And I got it working by reading these threads:

[http://backports.ubuntuforums.com/showthread.php?p=3594699#post3594699]("http://backports.ubuntuforums.com/showthread.php?p=3594699#post3594699")
[URL="http://ubuntuforums.org/showthread.php?t=585745"]
http://ubuntuforums.org/showthread.php?t=585745[/URL]

The solution was to edit a HAL script:   ```
 /usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux

```

by adding:
```

value="`expr $value / 19235509`"
```

to The beginning of the script.

This worked flawlessly.  I could unplug and plug the AC in repeatedly and the brightness would change to the correct settings every time.  I could manually adjust the brightness to my hearts content.

Now however, when I first start the computer with the AC plugged in the screen is displayed at full brightness.  Then I unplug the AC and the screen dims.  Wonderful!  But when I plug the AC back in, or try to adjust the brightness manually, there is no change in brightness.  The screen is stuck at the Battery power brightness level.  

Basically, if I dim the screen at all I lose control of my screen brightness (I can make it neither dimmer not brighter).  Even with the AC never being unplugged.  

I have some VERY basic knowledge of scripting, but the HAL scripts are a bit over my head.  I can get a basic idea of what they are doing, but can really understand how they work and interact with the system.

Any thoughts are welcome!


EDIT:  
I thought I would try removing the addition to the HAL Script, and sure enough, that fixed the problem.  This is very curious, because I had Ubuntu installed on this machine before with out ANY brightness problems, but then I had to replace the Hard Drive and on the newer install ran into the problem.  But now it seems that the default HAL settings work again.  Well see if it keeps on working...

---

### Post by BandD on 2008-03-10
Now my screen brightness is uncontrollable again by the default HAL settings.  However, if I edit that HAL script with the specified value, then everything is ok again.  

What is changing to make HAL need this other variable type?  Is there a way that I can monitor this?  Where should I begin looking?

It's not a huge deal, I'm just very curious.

---

