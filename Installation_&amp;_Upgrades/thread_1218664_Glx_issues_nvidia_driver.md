---
title: "Glx issues nvidia driver"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by jmerkin on 2009-07-20
Greetings. I am having some video driver issues in 9.04. I have an GeForce 9800 GT. I installed nvidia's proprietary driver and some errors popped up about GLX not being found and thus not installing. I finished the installation and started x. The driver seems to be working properly-ish. It loads and I can adjust the resolution to much higher than before. However, glxgears doesn't run and no desktop effects will work. The default window-goes-clear-while-moving doesn't even happen. 

Installing nvidia-glx-180 through apt does nothing, as it says it's the newest version. I've tried reinstalling the driver to no avail. I'm not sure where to go next. Anybody have experience with this? I found a forum post with the same problem and the guy solved it, but didn't post what he did..

---

### Post by jmerkin on 2009-07-24
bump

---

### Post by wojox on 2009-07-24
Post feedback:

```
lspci | grep -i nvidia
```

---

### Post by jmerkin on 2009-07-27
Greetings wojox

```
lspci | grep -i nvidia
```

spits out: ```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
```


That seems to be fairly normal to my not-so-experienced eye. However, ```
glxgears
``` gives me ```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

Not sure where to go from here. Thanks for suggestions.

---

### Post by jmerkin on 2009-07-30
bump? anybody?

---

### Post by tnc on 2009-07-30
well jmerkin, I'm gonna give a bump to this thread being as I have a similar problem.  

Where did ya find this "glxgears" thing?

Tim

---

### Post by sandy8925 on 2009-07-30
I don't really know much about this sort of thing but i'm pretty sure that the glx etension isn't getting loaded. Maybe your xorg.conf isn't properly configured. By the way i recommend you get the latest driver from nvidia's website and install that. drivers have recently become pretty awesome. post your xorg.conf contents here. It's in /etc/X11/xorg.conf

---

### Post by jmerkin on 2009-07-30
@tnc

glxgears is just a terminal command. my understanding is that when things are working properly, it displays some turning gears and the framerate like it does on my other computer. this computer isn't and glxgears spits out the error.

@sandy

the glx module isn't getting installed. i installed the most recent driver versions and they gave that error. i'm at work now, but will post my xorg.conf when i get home. i don't think the issue is there because during the driver installation using the nvidia script i got errors about glx libraries not being installed.

---

### Post by tnc on 2009-07-31
jemerkin: I tried that glxgears thingy and got the same result as you.

I looked at the file /var/log/Xorg.0.log and sure enough there it is: the glx extension is not being loaded just as sandy suggested.  the xorg.conf file has no reference to a driver at all.  I apt-get installed nividia-glx-legacy driver and no errors and no difference.  Weird eh?

Anyway, I'll stop hijacking your post now  :)   

Bump!

Tim

---

### Post by jmerkin on 2009-07-31
hi tnc

you're not threadjacking as far as i'm concerned. you're having the same problem as i am.

the legacy driver is only appropriate for older video cards. it's not for me since i'm working with a geforce 9800gt. if you go  [**here**]("http://www.nvidia.com/Download/index.aspx?lang=en-us") you can enter your card information and it'll spit out the correct driver. it seems that a new driver was released for me today, so when i return home i'll be installing that to see if there's any difference.

---

### Post by bbikebbs on 2009-07-31
I was having all sorts of problems with my FX5200.  Finally found this post:

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

which took care of things.  Imho, it was removing all of the drivers, etc. and reinstalling from a "clean" system that finally took care of things.  Just something else to try!

---

### Post by jmerkin on 2009-08-23
I got caught up in the end of summer, so I apologize for delaying so long in replying. I tried the newest version of the driver and it gave me the same issues. However, the beta 190.* version is a beautiful thing. Popped up with no glx issues and all the pretty graphic effects work (as does $glxgears).

And the post above this one is a pretty good guide for installing. I used that until following it further would have given me dependency issues. There's an OK package you can install envyng that will guide you through the already pretty hands-off driver installation as well.

---

### Post by tnc on 2009-09-22
An update from me as well:
It turns out my card is just really old.  The legacy drivers did work when I followed the above thread, however, the Ubuntu driver does a much better job.  The GLX thingy does work now.  All the fooling around led me to repairing something I wasn't even aware of before.  Fortunate side effect.... :)

---

