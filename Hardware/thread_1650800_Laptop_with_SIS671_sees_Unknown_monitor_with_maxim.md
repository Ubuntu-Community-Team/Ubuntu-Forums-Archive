---
title: "Laptop with SIS671 sees Unknown monitor with maximum 800x600 resolution"
date: 2010-12-22
forum: Hardware
---

### Post by hartz on 2010-12-22
My partner's laptop (A packard Bell MH35) just "crashed", which is to say that Windows Vista became unusable.  Due to the fact that the recovery process proved difficult (Missing recovery disks, etc) I am afforded a rare opportunity to install Ubuntu ... even if only as an interim measure.

I am of course motivated to make the Ubuntu experience as good as possible for her, so as a result I'm quite frustrated and under time pressure - if Ubuntu proves too difficult to get working well, then she will still want her Windows back.

Enter the dreaded SIS671 chipset.

From many similar questions I understand that there is no proper support for this chipset in Ubuntu.  Previous versions might even work better.  Some people have had some success with drivers that are not supported as part of the Ubuntu software, particularly on earlier distributions, but I shy away from one-man solutions in all but the most desperate of situations.

I have installed ubuntu 10.10 from a USB drive and updated it with patches, etc.

The screen however will not work at a resolution beyond 800x600.  xrandr says that that is the maximum supported screen resolution.  Numerous posts which instructs on how to use modelines to define and activate new modes all presume that xrandr is reporting a maximum resolution which is higher that the current active resolution.  Also the monitor is seen as "Unknown Monitor"

I have read that, and see that there is no Xorg.conf file any more. I also read that is should now be possible to create a minimal xorg.conf containing only the bits that are needed (eg to define the monitor).

So my first hope is to create an xorg.conf file which just defines the internal display panel - I believe the maximum resolution should be 1280x800.

If that still fails I expect a full xorg.conf would be the next thing I should try.

And then if that still fails I need to decide between using another Linux distribution which includes support for the SIS671 chipset, or trying to make and keep manually installed driver working...

My questions:
a) Have anybody managed to get this laptop, or for that matter any laptop with the SIS671 chipset, to work properly with Ubuntu 10.10, eg to get the full screen resolution available and to be able to use Compiz / pretty screen effects?  If so please explain what your steps were.

b) Does anybody have suggestions about how to set up xorg.conf, ideal if your suggestion keeps in line with the new minimalistic xorg.conf objective (but not an absolute requirement) 

c) What other words from the wise?  Even if suggesting another pretty, modern, gnome-based Linux distribution?

Thank you,
  _Hartz

---

### Post by sanderj on 2010-12-22
I would say Linux support for the SIS671 is ... hopeless.

I've a laptop with a SIS671, and via-via I was to able to get a driver for Ubuntu 7.04/.10. After that, I've given up. No more SIS for me.

Here's the blog of a SIS employee:
[http://barroslee.blogspot.com/2007/11/release-sis-671sis-672-linux-3d-driver.html](http://barroslee.blogspot.com/2007/11/release-sis-671sis-672-linux-3d-driver.html)

A lot of people ask him for the driver. I don't know if they have any success

---

### Post by IcarusR on 2010-12-22
This link should help you create an xorg.config...

[http://www.grenage.com/xorg.html]("http://www.grenage.com/xorg.html")

Also could try using xrandr to set resolution.

Info on how to use xrandr here

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

---

### Post by sanderj on 2010-12-22
@hartz: maybe there is hope: [http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)

---

### Post by hartz on 2010-12-29
@all responders: Thank you.  I have read all these pages as part of my own research.  They don't answer my questions - setting screen resolution with xrandr requires it to believe the display capable of a mode.

In my case xrandr reports the MAXIMUM resolution as 800x600.  Others have had the same results - trying to set up a mode for a larger display results in an error.

The answer seems to lie here: [http://www.petitiononline.com/sislinux/petition.html](http://www.petitiononline.com/sislinux/petition.html)

Cheers!
  _hartz

---

