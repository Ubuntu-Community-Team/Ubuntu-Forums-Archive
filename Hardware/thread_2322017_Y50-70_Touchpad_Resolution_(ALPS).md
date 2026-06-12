---
title: "Y50-70 Touchpad Resolution (ALPS)"
date: 2016-04-25
forum: Hardware
---

### Post by ryan214 on 2016-04-25
Hello! This is my first post in Ubuntu Forums. I am hoping someone could give me some direction and/or advice...
I have a new Lenovo Y50-70 and am having one major issue, the touchpad. The resolution is wrong in relation to the screen. The X axis seems to be fine, but the Y axis moves way too slow. It seems like there should be a simple fix, one which eludes me. It seems as though i just need to increase the Y sensitivity. I found a post somewhere which told me to:

modify /usr/share/X11/xorg.conf.d/50-synaptic.conf (i think that's right, going off memory)
and add: option "VertResolution" "75", option "HorizResolution" "75"
but these made no difference. I tried changing several different values, but none changed anything. (rebooted between changes)

but this advice was for Ubuntu 10ish so that's probably why it didn't work.

This is where i got some of the things that i tried...
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
And the other site:
[https://dottheslash.wordpress.com/2011/11/18/touchpad-sensitivity-differs-with-aspect-ratio/](https://dottheslash.wordpress.com/2011/11/18/touchpad-sensitivity-differs-with-aspect-ratio/)

Thanks in advance for any attempt at helping me!
This laptop runs ubuntu very well (except for really bad screen tearing while using nvidia gpu, maybe i'll try to fix that next)


At this point, i'm considering using evdev to grab the trackpad, add extra y movement, then inject. LOL. I Know.

---

### Post by psico111 on 2017-01-18
Same problem here, but I can't enable/disable touchpad with Fn+F6 shortcut, All this problems presented after the first update, in the clean install and live cd I dont have problems. (I'm in ubuntu 16.04.1)

I check in a lubuntu live version (16.04) and all works. But I dont use lubuntu for day to day, only I do it for testing.

---

