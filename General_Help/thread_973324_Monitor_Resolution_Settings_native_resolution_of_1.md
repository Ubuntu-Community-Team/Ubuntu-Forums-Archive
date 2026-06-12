---
title: "Monitor Resolution Settings: native resolution of 1680x1050 not there"
date: 2008-11-06
forum: General Help
---

### Post by TheShocker on 2008-11-06
Hello, I have a question about monitor resolution.

I have a 1680x1050 monitor but that resolution is not an option in Monitor Resolution Settings.

I am running Ubuntu 8.10 and I have this hardware:

GeForce 8600 GT - [http://www.newegg.com/Product/Product.aspx?Item=N82E16814150260](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150260)

Acer AL2216Wbd 22" Widescreen LCD Monitor (1680x1050 native res) - [http://www.newegg.com/Product/Product.aspx?Item=N82E16824009094](http://www.newegg.com/Product/Product.aspx?Item=N82E16824009094)


What do I need to do to set the proper resolution?

Thanks

---

### Post by genconcu on 2008-11-06
I've had the exact same problem and I solved it not ten minutes ago. Here is what I did:
1) I installed Ubuntu 8.04.
2) I installed Envy.
3) I installed Nvidia driver 173 manually.
4) After restart, I ran "sudo displayconfig-gtk" in the terminal.
5) From the Screens & Graphics window, I chose my monitor as "Generic 1680x1050 widescreen"
6) I copied my xorg.conf file to another place (i.e. sent it to myself via email).
7) I installed 8.10.
8) I installed Nvidia driver 173 via Hardware Drivers (since I had installed 173 in 8.04; I don't know if this method works with 177 driver)
9) I replaced xorg.conf with my previously copied xorg.conf file from 8.04.
10) I restarted and it worked :) Now I have 1680x1050 resolution.

Hope this helps.

---

### Post by Maconvert on 2008-11-06
Thanks for the info.
However, what do you do if you're performing a fresh install of Ubuntu 8.10?
There's got to be a way to set my resolution to 1680 x 1050.
By the way, I typed "sudo displayconfig-gtk" in the terminal and it told me "command not found". I installed "Envy" first.

---

### Post by shazbut on 2008-11-06
It may sound silly, but have you tried using the DVI connection on the monitor?  I know my 1680x1050 montior + nvidia card had troubles detecting the correct resolution when I was using an analogue VGA cable, but changing to a DVI-DVI cable and restarting X fixed it straight away.  Of course that's not much help to you if you don't have such a cable.  My workplace seemed to have boxes of them lying around though, for some strange reason people seem to prefer the familiarity of the old VGA connector.

---

### Post by genconcu on 2008-11-07
> **Maconvert said:**
> Thanks for the info.
However, what do you do if you're performing a fresh install of Ubuntu 8.10?
There's got to be a way to set my resolution to 1680 x 1050.
By the way, I typed "sudo displayconfig-gtk" in the terminal and it told me "command not found". I installed "Envy" first.


I had made a fresh 8.10 install, but I couldn't set my resolution to 1680x1050 in any way. I tried adding it manually to xorg.conf, but then the monitor gave an out of range error after restart. The reason I installed 8.04 first is that I had the same problem in 8.04 and I was able to solve it via displayconfig-gtk. But this tool didn't find its way into 8.10, a bad decision I must say. This brings us to- did you use "sudo displayconfig-gtk" in 8.04 or 8.10? 8.10 does not have that tool, so that may be the reason of error message.

shazbut also has a point. my monitor has only analog output, that may be the reason behind this problem. try using DVI-DVI cable if your monitor has DVI output.

---

### Post by Maconvert on 2008-11-07
That's a good point about the DVI cable.
However, I'm using an analog KVM and I want to only use this PC connected via VGA.
Possibly if I just connect it once then Ubuntu will set everything up to allow me to use 1650 x 1080.
Then I can switch it back over to the VGA connector and it will still work.
I'll try it in the next couple of days.

Cheers!

---

### Post by TheShocker on 2008-11-08
Actually, I am using the DVI cable.

Thanks for the success story genconcu, but there has got to be a way to do this without installing an older version of Ubuntu first...

Seth

---

### Post by TheShocker on 2008-11-11
Is there not another way to simply get my monitor resolution to work?

---

### Post by iggames on 2008-11-12
You could try using xrandr to manually add and set the resolution. First, run ```
xrandr
``` in a terminal to see what your displays are named. On my laptop, I get the following:

```

$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x1024+0+0 (normal left inverted right x axis y axis) 285mm x 214mm
   1280x1024      60.0* 
   1280x960       60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)

```

In this case, LVDS is the name of my laptop's internal display. Try adding the resolution manually:

```
xrandr --addmode LVDS 1400x1050
```

If that works, then you can try setting it with:

```
xrandr --output LVDS --mode 1400x1050
```

That said, this isn't working on my laptop at the moment...but it gives you something to look up, at least. Good luck!

---

