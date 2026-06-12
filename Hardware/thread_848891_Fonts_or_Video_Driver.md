---
title: "Fonts or Video Driver?"
date: 2008-07-03
forum: Hardware
---

### Post by -Outcast- on 2008-07-03
I have a sony vaio TZ series running HH

I have installed the MS Times Font collection (sorry forgot the name of the package) 

I have fonts set to smooth on lcd and have tried the other options too. 

I use ooo writer a lot. 

There is definitely something up with my fonts or display. Even with some webmail I have the same issue. 

The font appears a little off. Sometimes one letter is a little darker than another, and they look a tiny bit stretched. 

It's enough to make it distracting. I thought it was the font issue. Until I installed the package with Times in it. Still the same. So I thought it the drivers for my video card or MB. But then DVD and video play perfect and everything else is fine. Just fonts. 

I have been around the ooo forums and have tried various things there, but no go. Plus the fact that it effects some of my webmail brings me back to either the system fonts or display. 

Anyone got any ideas?

Thanks

---

### Post by -Outcast- on 2008-07-04
[http://ubuntuforums.org/showthread.php?p=5316548#post5316548](http://ubuntuforums.org/showthread.php?p=5316548#post5316548)

HAve been using this thread to no avail

---

### Post by masterpo on 2008-07-04
I to have this problem .

 Some of the font are darker and even little parts of the same letters may even be darker and lighter. 

  I am leaning towards Driver problem . It started when I was working with " wine " and DX9. 

I have searched to no avail and reloaded fonts ( also MSfonts ) .
  
 I did notice that when I was adjusting my monitor that it was detecting a different resolution than what the nividia driver setting where set for. I don't know if that really means anything . But.. at this point am am shooting at shadows . 

If I bold the fonts of course there is no problem . But if I goto a webpage or even rdp to another computer . The default fonts there will have the same problem on my screen but of course they are fine on the other computer . 

LOL If I find out what it is I will be sure to post it -Outcast-. 

 I would sure appreciate it if you do the same .

---

### Post by -Outcast- on 2008-07-04
Have spent 4 straight hours on this thing now. Followed lots on the forums and not a thing comes close. I spend hours on writer and it's really effecting me. I am going to have to head back to 7.10. I don't think there were so many issues there. 

Will post back if I come up with anything in the mean time. Seems like its an issue on HArdy

---

### Post by masterpo on 2008-07-06
I never did find the problem. 

I reinstalled:

nonfree video drivers 

All Fonts ( and M$corefonts )

I set font dpi in the Xconf as well as screen resolutions and refresh rates ( I tried 96 through 105 dpi ). 

I yelled at the computer and called it mean names 

I tried smacking the screen with an Iron Skillet .

So then I activated Secret Red Plan B !

**********************
 Secret Red Plan B  ( AKA Shotgunning )

Run rsync on on back up directory and home directory to predefined  backup media.

 Reinstall OS

**********************

Now I am usually a person you like to figure out what is wrong and learn from the fixing it . 

But I have invested over four hours of time when all it took what a 10 minute install and 5 minute rsync to get me rolling again . 



Sorry This problem remains a mystery for now .

---

