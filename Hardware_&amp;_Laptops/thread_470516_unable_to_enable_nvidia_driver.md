---
title: "unable to enable nvidia driver"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by karmaraver on 2007-06-11
I updated the other day when update manager notified me of header files that were out of date. i update and restart and i notice my screen resolution is 1024x768 when it's supposed to be 1680x1050. i check in preferences > screen resolution and 1680x1050 is no longer available. i also notice that the binary nvidia driver is no longer enable in the restricted driver manager. when i attempt to enable and restart, the xserver can't start until i run
```
sudo dpkg-reconfigure xserver-xorg
```
afterwards the xserver starts and i'm back with 1024x768 and the binary nvidia driver still disabled.

what could changing the header files have changed that would effect the drivers or xorg? also what might i do to get myself out of this conundrum :(

I'm running fiesty, kernel 2.6.20-15-lowlatency (for ubuntu studio) although no kernel will work.

any ideas? suggestions? i'd be happy to post any relevant information, but i don't know much about what is relevant.

---

### Post by Kobalt on 2007-06-11
There can be a few hiccups using the Restricted Drivers Manager. What you can do is open up Synaptic package manager and install the nvidia-glx (or nvidia-glx-new, depending on your graphic card). Then run ```
sudo nvidia-xconfig
```And finally, if you still don't get your proper resolution, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Select "nvidia" as driver if asked, then select the resolutions you want as available by hitting the spacebar. Validate, and then restart X with Ctrl+Alt+Backspace so that the changes take effect. 

That should do it.

---

### Post by karmaraver on 2007-06-11
thanks, that did work :D i'm using nvidia-glx-new now and i have the proper resolution.

only problem now is i don't get borders or title bars when using beryl, but i'm guessing that a whole other deal. i'll probably figure that one out with searches and all that.

Thanks!!

---

