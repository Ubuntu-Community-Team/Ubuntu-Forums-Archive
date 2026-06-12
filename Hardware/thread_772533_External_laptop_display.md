---
title: "External laptop display"
date: 2008-04-28
forum: Hardware
---

### Post by Bukes on 2008-04-28
I'm trying to accomplish something that should be relatively simple:

I've installed Hardy on my Think Pad T60p (ATI FireGL 5200) laptop which has a native display resolution of 1400x1050.  My docking station has a monitor attached that supports 1600x1200.  

Naturally, I'd like the laptop to behave as Windows does - automatically use the maximum screen resolution available, depending on the capabilities of the screen that is attached (docked/undocked).

I'd settle for the next best thing - manually selecting the resolution via Preferences->Screen Resolution.  Problem here is that the resolution combo box doesn't have 1600x1200 as an option.

Anyone know how this combo-box is populated, or how to get 1600x1200 to appear?

Thanks in advance

---

### Post by treyphan on 2008-05-29
if you can post your xorg.conf I might be able to give you some tips. I am still fighting with my t60p ATI card on a lot of things but I have been able to make some breakthrough along those lines.....

---

### Post by jcsteele on 2008-05-29
You also might want to check out xrandr ... it will allow you to query the external monitor and see what resolutions it is telling your machine are available...you can also force it to use that resolution with xrandr.

Example:

$ xrandr -q   (this will let let you if your output medium is detected.)
$ xrandr --auto (this will setup the output medium and the appropriate resolution)
$ xrandr --output VGA --mode 1600x1200 (Force it to use 1600x1200 resolution)

This is for my laptop...your output might not be "VGA" in the last command...you will have to check with xrandr -q to find out your exact specifics.

Hope this helps...its not a GUI solution, but at least "it works"

---

### Post by treyphan on 2008-05-29
hmm that actually helps me I think.. I've never been able to get ubuntu to recognize my default screen either, it always just says "unknown" and I've never been able to get "big screen" to work right.. I tried several different options and really need clean my xorg.conf up but haven't found a good way to experiment... LOL 

If you have any good hints on xorg.conf experimentation, feel free to share :)

---

### Post by jcsteele on 2008-05-29
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf)

---

### Post by treyphan on 2008-05-30
Great.. reading it now. Thanks a billion for your help :) I have about 10 years of windows Engineering under my belt but have completely switched over to Ubuntu for desktop/laptop use "plus a few of our servers just recently". 

It blows me away how good Ubuntu is...

---

