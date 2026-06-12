---
title: "Screen Rotation with a tablet PC?"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by mapage on 2006-06-09
I have a Toshiba Tecra M4 Tablet PC that I have installed Ubuntu on and would like to make 'fully functional'  

I've read a couple of posts that describe how to rotate the screen, but they all seem to require X to be restarted.  (Closing all open apps in the process)

Is there a good way of rotating the screen without having to restart X?  If not, is there a 'best' way to set up the screen rotation in the xorg.conf?

Also, do you have or know of any sort of utility that will allow you to map the tablet PC screen buttons to user defined actions?  (Script files, or whatever...)

One last question, there is some sort of mercury switch (or whatever) inside the screen that tells it what the orientation of the Tablet PC is, have you heard of anyone being able to tap into it to know which way is up?

(I think you can see the direction these three questions are heading...)

---

### Post by 23meg on 2006-06-09
[QUOTE=mapage]
Is there a good way of rotating the screen without having to restart X?  If not, is there a 'best' way to set up the screen rotation in the xorg.conf?
[/quote]Sure, there's xrandr. Check its manpage for details. For it to work with the proprietary nvidia driver you need to add the following option to the "Device" section of your xorg.conf file: ```
Option "RandRRotation" "True"
```

> Also, do you have or know of any sort of utility that will allow you to map the tablet PC screen buttons to user defined actions?  (Script files, or whatever...)Did you try if they work as normal keyboard shortcuts (in System / Preferences / Keyboard Shortcuts)? If they don't work as expected, try choosing "Super is mapped to the Win-keys" in System / Preferences / Keyboard.
> 
One last question, there is some sort of mercury switch (or whatever) inside the screen that tells it what the orientation of the Tablet PC is, have you heard of anyone being able to tap into it to know which way is up?
Your M4 has an accelerometer inside but AFAIK there's no support for it in the Linux kernel yet, so it can't be utilized. I'm also not aware of any way to detect the screen swivel event of the tablet PC (I had asked this before [here]("http://ubuntuforums.org/showthread.php?t=102994"))

---

### Post by mapage on 2006-06-09
[QUOTE=23meg]Sure, there's xrandr. Check its manpage for details. For it to work with the proprietary nvidia driver you need to add the following option to the "Device" section of your xorg.conf file: ```
Option "RandRRotation" "True"
```
[/QUOTE]

Works perfectly!  Thanks!

[QUOTE=23meg]
Did you try if they work as normal keyboard shortcuts (in System / Preferences / Keyboard Shortcuts)? If they don't work as expected, try choosing "Super is mapped to the Win-keys" in System / Preferences / Keyboard.
[/QUOTE]
It did work.  To bad there isn't a way to run an arbitrary program instead of having just the options listed there.  Maybe there is and I just didn't see it.

[QUOTE=23meg]

Your M4 has an accelerometer inside but AFAIK there's no support for it in the Linux kernel yet, so it can't be utilized. I'm also not aware of any way to detect the screen swivel event of the tablet PC (I had asked this before [here]("http://ubuntuforums.org/showthread.php?t=102994"))[/QUOTE]

I looked at your message.  NO replies!  Ouch!  I wonder how many Ubuntu Toshiba M4 users there are out there?

Thanks for the help!

---

### Post by 23meg on 2006-06-09
> It did work.  To bad there isn't a way to run an arbitrary program instead of having just the options listed there.  Maybe there is and I just didn't see it.
Sure there is.

[http://ubuntuforums.org/showthread.php?t=42404](http://ubuntuforums.org/showthread.php?t=42404)
> 
I looked at your message.  NO replies!  Ouch!  I wonder how many Ubuntu Toshiba M4 users there are out there?Not many I guess. I asked on the Gentoo forums too, and no replies from there either. The M4 is quite a Linux friendly machine though; everything except the IR port (which I haven't tried) works.

> Thanks for the help!
You're welcome.

---

### Post by 23meg on 2006-06-09
For more info on Linux on tablet PCs check out these two sites:

[http://tuxmobil.org](http://tuxmobil.org) (lots of well written guides)
[http://tabletpcbuzz.com](http://tabletpcbuzz.com) (active general forum with some knowledgeable Linux users)

---

