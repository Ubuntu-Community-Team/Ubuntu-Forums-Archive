---
title: "External screen blanks every ~9 secs for 1 sec"
date: 2010-11-02
forum: Hardware
---

### Post by belgianfries on 2010-11-02
Hello,

I am connecting an external LCD screen via VGA cable to my laptop with an ATI Radeon X1600 card, using the default "radeon" driver, on Ubuntu 10.10.
The external screen works, it shows up in the screen configuration, but it is "Unknown" and the resolutions are wrong/missing. The internal screen works normal.
The problem is that the external screen blanks at regular intervals of about 9 seconds for 1 second (also if I add the correct resolution manually using xrandr).
I have the suspicion that this is due to the screen being continuously probed. When I click the "Detect screens" button in the screen configuration or run "xrandr -q", it blanks the same way.

From what I could find out, randr in Xorg could be responsible for that. I tried to disable it in xorg.conf with no success:

        Option "NoRandr" "yes"
        Option "RandR" "false"
        Option "EnableRandR12" "false"

Can anyone confirm that randr is causing the screen blanking and does anyone know if it is possible to turn it off or fix the problem in some other way?

In previous Ubuntu versions the external screen/dual screen worked fine. Also, when I connect a HD TV via DVI/HDMI using 10.10, it works perfect.

Cheers,
Torsten

---

### Post by sanderd17 on 2010-11-02
Hi belgianfries (just ate some yesterday :P ),

can you try to uninstall the proprietary driver? Just use the Open source driver, you can choose your screen configuration with the program grandr (gnome frontend for randr). I believe randr can't communicate very well with the proprietary driver.

---

### Post by belgianfries on 2010-11-03
Hello sanderd17,

Thanks for the quick reply (I didn't have fries for a while actually ;-).

With the proprietary driver, you mean the fglrx driver from ATI? I don't use that one, it does not support old cards like mine any more.
I am using the default radeon driver that comes with Ubuntu.

I thought about trying the radeonhd driver and see if that changes anything.

Torsten

---

### Post by sanderd17 on 2010-11-03
Sorry, I thought you meant the proprietary driver ubuntu sometimes propose.

do you use compiz?

maybe removing compiz helps:

```

sudo aptitude remove compiz

```

---

### Post by belgianfries on 2010-11-04
Nope, Compiz is not the problem.

I read somewhere that disabling randr in xorg is kinda pointless, because it enables it anyway if it is required. The only way to really disable it seems to compile xorg without randr support. But I don't feel like doing that :-)

Cheers!
Torsten

---

### Post by sanderd17 on 2010-11-04
well, it's xrandr that lets you switch the screens, so without xrandr, you wouldn't be able to connect an LCD screen. But I believe the problem is a bug in xOrg, so it will be hard to fix, I can't help you any further.

---

### Post by sanderd17 on 2010-11-04
or wait a while, you could use xVesa instead of xOrg. I thought ubuntu couldn't use xVesa but it seems possible. Go to the link in my signature about setting boot options and try to set the option "xforcevesa" (without quotes), first try it temporarily, if it works, make it permanent.

---

### Post by belgianfries on 2010-11-04
I might give it a try, but I wonder if you can get a dualhead configuration to work with vesa.

It is by the way perfectly possible to do that with xorg without (x)randr - then it just has to be configured in xorg.conf the "old" way.

It is not a big problem that I can't connect the external screen, it is just a shame because it worked fine before.

Torsten

---

### Post by sanderd17 on 2010-11-04
well, vesa is for low end graphics, so I don't know it either. I agree with you that it's a shame that it worked before.

---

### Post by belgianfries on 2010-11-04
But there is hope it might work again one day :-)

A bit too many regressions in the recent past for my taste, but in general things work better and better with every release - and it is Linux, after all!

Torsten

---

