---
title: "How to disable touchpad tapping in X?"
date: 2009-01-21
forum: Hardware
---

### Post by InspiredIndividual on 2009-01-21
Despite having tried several different possible solutions I found on the web, I still haven't managed to disable touchpad tapping on my laptop. This behaviour is very annoying, and I hope someone may have an idea what else I can try.

I've got Ubuntu 8.10 Intrepid Ibex 64bit installed. In Gnome, I can manage to disable touchpad tapping quite easily in System > Preferences > Mouse. The problem is that my laptop is old and slow and I prefer snappy performance, so I mostly do not use Gnome. Unfortunately, if I disable tapping in Gnome, this doesn't apply to other Desktop environments or Window Managers. I mostly use IceWM, but I don't understand exactly why this matters. I thought X takes care of the communication with the hardware in all cases, so what window manager you use doesn't matter. I'm probably wrong, but I don't understand why. Another possible solution I tried was to edit xorg.conf manually. However, the file doesn't contain a section on my touchpad. Adding such a section manually made no difference whatsoever. A third possibility I found in some of the many posts on this issue was to use gsynaptic (or a similar GUI) to configure the behaviour. Unfortunately, this also failed. I got the following error message: ```
GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
``` I did so, but this didn't make any difference.

There are loads of questions and answers about this issue in several fora around, but all solutions I found so far seem to focus on the three possibilities I've tried already. Does anyone have an idea what more I could try?

---

### Post by InspiredIndividual on 2009-01-26
I was a bit busy, so it took a while until I found more time to try and solve this issue. Finally I found the solution in the following thread: [http://ubuntuforums.org/showthread.php?t=949976](http://ubuntuforums.org/showthread.php?t=949976). I had a different Touchpad than the poster there, so my line to add to my startup list was a bit different: 
```
xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Synaptics Tap Time" 32 0
```

If some other newbies stumble along this thread, the following is why I did find the solution now and couldn't find it earlier. It seems my problem was version specific, so adding my Ubuntu version (in my case 'Intrepid') to my google search did the trick.

---

