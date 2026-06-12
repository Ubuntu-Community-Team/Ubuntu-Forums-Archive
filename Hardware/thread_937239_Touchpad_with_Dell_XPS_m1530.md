---
title: "Touchpad with Dell XPS m1530"
date: 2008-10-03
forum: Hardware
---

### Post by k3nz13 on 2008-10-03
I have installed ubuntu on my dell xps m1530 laptop, and everything works fine with the exception of the touchpad.

It is either buggy and all over the place or extremely slow moving. When it is just slow-moving, it is at least USABLE, but it takes a long time to do anything productive due to the incredibly low sensitivity of the touchpad.

I have tried installing gsynaptics and editing the xorg.conf file (setting CMHConfig to both "true" and "on") with no success. I simply get an error message on startup of gsynaptics telling me to enable CMHConfig before using.

Is there any way to actually get gsynaptics or another touchpad driver working?

If not, is there simply some xorg fix that I can use to increase the sensitivity of the touchpad?

Thanks!

---

### Post by k3nz13 on 2008-10-03
Wooo! I feel like such a champion, I finally got the synaptics driver to work!

Here is what I did (completely unintentional, actually).

I was noticing that gsynaptics wasn't working because apparently SHMConfig wasn't set to true. I knew, however, that in my xorg.conf file, it was in fact set to true under the synaptics touchpad device section.

Thus, I figured, it wasn't recognizing the touchpad as such. I then added SHMConfig "true" at the top of the configuration file, under something that I knew was executing (this is completely pointless, as I realize now [I'm a linux-noob]), and when I booted up again, my graphics drivers didn't load, putting me in low-graphics mode. HOWEVER, my touchpad started working!

I then reinstalled the nvidia drivers, rebooted, and both my touchpad and graphics drivers work! I can even enable scrolling and sensitivity settings within the config now!

That was quite the adventure, but it worked! For someone suffering from the same seemingly irrepairable issue as me, give it a try, who knows!

---

### Post by slyhne on 2008-10-15
Hey

Could you try to post your working xorg.conf here?

I'm having the same issues as you had, and any help is welcome.


Regards
slyhne

---

### Post by shahryary on 2008-10-29
> **k3nz13 said:**
> Wooo! I feel like such a champion, I finally got the synaptics driver to work!

Here is what I did (completely unintentional, actually).

I was noticing that gsynaptics wasn't working because apparently SHMConfig wasn't set to true. I knew, however, that in my xorg.conf file, it was in fact set to true under the synaptics touchpad device section.

Thus, I figured, it wasn't recognizing the touchpad as such. I then added SHMConfig "true" at the top of the configuration file, under something that I knew was executing (this is completely pointless, as I realize now [I'm a linux-noob]), and when I booted up again, my graphics drivers didn't load, putting me in low-graphics mode. HOWEVER, my touchpad started working!

I then reinstalled the nvidia drivers, rebooted, and both my touchpad and graphics drivers work! I can even enable scrolling and sensitivity settings within the config now!

That was quite the adventure, but it worked! For someone suffering from the same seemingly irrepairable issue as me, give it a try, who knows!

hi,
please try to post your working xorg.conf  .
thanks .

---

