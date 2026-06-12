---
title: "Lenovo Thinkpad x60 tablet problems"
date: 2009-01-30
forum: Hardware
---

### Post by Andcor on 2009-01-30
Hi
I've just reinstalled my Lenovo thinkpad tablet computer because I wanted a dual-boot with windows. However when I had installed ubuntu 8.10 all over again I tried with the old xorg.conf in order to get the wacom tablet to work again. This worked fine until I made an dist-upgrade and then X starts in "low-graphic" mode (still 1400x1050 but without tablet support) and my xorg contains this line:
```

(**) Option "FlowControl" "Xoff"
[COLOR="Red"]usbDetect: can not ioctl version[/COLOR]
(==) Wacom using pressure threshold of 15 for button 1

```

Any help that could get my tablet working again would be appreciated.

Regards

Andreas

P.s. I have attached the whole Xorg.0.log and the xorg.conf

---

### Post by Andcor on 2009-01-30
Can't anybody help me. Is my only solution to reinstall ubuntu and wait for a better xorg, wacom driver or kernel to come into apt-get?

Andreas

---

### Post by Andcor on 2009-01-30
I have now tried to reinstall the linux-wacom software (both the latest stable and testing) using the guide found here: [https://help.ubuntu.com/community/Wacom/LatestDriver]("https://help.ubuntu.com/community/Wacom/LatestDriver").
It did, however not change anything. Can the problem be kernel related?

Andreas

---

### Post by Andcor on 2009-02-01
I have found out that the problem IS kernel related. When I boot up using the kernel from before the update I have no problem using the tablet device. But then the fingerprint reader won't work as this device is related to the latest installed kernel.

---

### Post by posburn on 2009-02-25
Hi Andreas,

Sorry nobody ever picked up your thread.  I just wanted to chime in to say that I've been feeling your pain.  I have a X60 tablet with a docking station, and the stylus would work fine if I wasn't docked, but upon booting while docked, Ubuntu would always start in low graphics mode.  The only way to fix this was to remove the wacom-relevant lines from my xorg.conf UNTIL....

I downloaded and compiled the latest wacom drivers from []("http://linuxwacom.sourceforge.net/") and now it seems that this version gets along with kernel 2.6.27-12-generic!  Everything is working fine, whether I'm docked or not.  Yay!

Not sure if you've solved your issues, but I'd suggest getting those newer wacom drivers and seeing if that helps.

Cheers,
Phil

---

### Post by jmexia on 2009-03-06
Hi, 

Just wanted to say that I'm suffering from the same problem here.  I had my X60 for awhile and have only recently installed Ibex on it.  I made changes to my xorg file and got the stylus working.  I ran and installed updates and when rebooting, got the "low-graphics mode" message.  I'm doing a clean install right now to get the stylus functioning again.  Any other ideas?

J.

---

### Post by Andcor on 2009-03-10
You could just do as I did, rearrange the boot order so that you boot on the old kernel. This works quite ok.

---

