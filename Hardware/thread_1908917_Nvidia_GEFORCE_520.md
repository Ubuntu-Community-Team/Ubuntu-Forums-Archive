---
title: "Nvidia GEFORCE 520"
date: 2012-01-14
forum: Hardware
---

### Post by shashanksingh on 2012-01-14
Hi.

I recently attatched an Nvidia Ge-Force 520 graphic card.

After booting in ubuntu, the graphics went bad.

I went to additional-drivers and installed the one it recommended.

After that, the graphics are still not upto the mark.

The resolution is just 1152x864, whereas in windows I get around 1300x900 something I guess.

The screen lacks sharpness, and when I try to modify somethings in the Nvidia X server settings (All I can understand is the resolution, but even the colour depth is 24 bits I guess, with 16 million; why not 32?)

Can someone pls just guide me how to tweak it?

64bit, Ubuntu 11.10

---

### Post by MoreOrLess on 2012-01-14
24-bits is really 32 in xorg speak. Don;t worry about that part.

---

### Post by papibe on 2012-01-14
There's a couple of things you can try, but first backup your X configuration file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then, try recreating your X configuration file by doing:
```
sudo nvidia-xconfig
```
after that restart your computer.

If that doesn't work, another option would be to update your driver for a more recent one:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
You may want to try recreating your xorg.conf again (as above), and then restart your machine.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by shashanksingh on 2012-01-15
Thanks. :)

I deleted the xorg.conf and a new one got created.

But since the graphics arn't even as good as the ones without the card, I thought of installing the drivers from the Nvidia Website. And now I ran into another problem...

[http://ubuntuforums.org/showthread.php?t=1909312](http://ubuntuforums.org/showthread.php?t=1909312)

---

### Post by papibe on 2012-01-15
If I were you, I would try the ppa first, and left the one from the Nvidia site as a last resort.

BTW, I commented your other thread.
Regards.

---

### Post by shashanksingh on 2012-01-15
> **papibe said:**
> There's a couple of things you can try, but first backup your X configuration file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then, try recreating your X configuration file by doing:
```
sudo nvidia-xconfig
```
after that restart your computer.

If that doesn't work, another option would be to update your driver for a more recent one:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
You may want to try recreating your xorg.conf again (as above), and then restart your machine.

Hope it helps, and tell us how it goes.
Regards.

I first installed from the ppa, did an upgrade.
So it came back to the same point where I started. 1024x768, 24 depth (If thats actually 32)

I tried installing from the nvidia website, n u were right... bad idea. It got worst.

So im back again, unsatisfied but atleast its ok now, with the drivers that jockey-gtk showed were available..

Thanks a lot for ur help @papibe :) 

Just two last things.. I cant reduce the size of the launcher icons..

I followed everything [ in this manual]("https://help.ubuntu.com/11.04/ubuntu-help/unity-launcher-change-size.html"), and I had even done it before.

Does that have anything to do with my new graphics card?

I would atleast like retain the small icon-size if not the awesome graphics.

And second, is there a setting to increase the sharpness a bit? The text, font on this resolution seem to be a bit hazy....

Thanks a lot again :)

Thanks

---

### Post by shashanksingh on 2012-01-15
I just checked, I think no other effect from compiz is working...

Is it due to the new driver?

---

### Post by papibe on 2012-01-15
Could you post your /var/log/Xorg.0.log ?

Paste it here [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post the link.

It may be give us some clues about what's going on.

Regards.

---

### Post by shashanksingh on 2012-01-16
Here it is.

[http://paste.ubuntu.com/806246/](http://paste.ubuntu.com/806246/)

Sorry I missed the tiltle.

Its my Xorg.0.log

---

### Post by frogotronic on 2012-01-16
> **shashanksingh said:**
> Thanks. :)

I deleted the xorg.conf and a new one got created.

But since the graphics arn't even as good as the ones without the card, I thought of installing the drivers from the Nvidia Website. And now I ran into another problem...

[http://ubuntuforums.org/showthread.php?t=1909312](http://ubuntuforums.org/showthread.php?t=1909312)

NNNNOOOOOOOO!!!!!!!!!!!!


Just Kidding - It's MUCH, MUCH better to use the XORG EDGERS PPAs for nVIDIA drivers.

---

### Post by papibe on 2012-01-16
```
[    27.716] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
```
It looks like either your monitor has a corrupt EDID (data with resolutions and timings supported), or they are not retrievable using a VGA cable.

Does your monitor and card support HDMI or DVI connections?

Sometimes using a digital connection (DVI for example) solves this kind of problems.

Regards.

---

### Post by shashanksingh on 2012-01-17
I do have an HDMI cable and the card supports it as well. But I tried HDMI in windows.. Connecting the cable and going to the HDMI AV option of the monitor (Actually, my monitor is a TV, it just has a CAT and HDMI option, it has a remote control :P) and all I got is the wallpaper.. No mouse and anything else.

I guess I just don't know how to use it.
:-/

---

