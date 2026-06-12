---
title: "Mouse not working on Ubuntu 16.04.1"
date: 2016-08-07
forum: Hardware
---

### Post by MZ250Supa5 on 2016-08-07
Just done a fresh install of 16.04.1. When I was using the live disc, the mouse was working fine. However, once booted into the installed version the mouse does not work. Did a bit of searching and came across this thread[http://askubuntu.com/questions/763511/usb-mouse-not-working-after-installing-ubuntu-16-04-persistent-fix]("http://askubuntu.com/questions/763511/usb-mouse-not-working-after-installing-ubuntu-16-04-persistent-fix"). I followed the directions included there, and the mouse works, however, as pointed out there, this does not make it persistent.  There is no mention of a fix there, and I was wondering if indeed there is a fix.  

I've also installed the drivers for my Hanvon graphics tablet, and whilst I can see where it moves on the desktop, when moving the stylus, the cursor arrow completely disappears. I'm thinking this is related. The keyboard works fine.

Is anyone else experiencing this issue?

---

### Post by him610 on 2016-08-08
Once in a blue moon, my Logitech USB mouse seems to die. Unplugging it followed by plugging it back in usually brings it back to life.

---

### Post by MZ250Supa5 on 2016-08-09
The first thing I tried was the unplugging and plugging back in thing - it's become second nature!  However, it seems that this is only partially successful, as I've found that whilst there is some movement detected, and sometimes the cursor will move, the operation is erratic until I type in the commands in the terminal.  It may be that I need to use a different USB socket, but that would mean that Ubuntu is becoming as temperamental as Microsoft when it comes to plugging in peripherals!  I truly hope it hasn't come to that!!

I'm about to rebuild this system anyway, and install a pci USB card as I need many more USB sockets than I presently have.

---

### Post by dmkonlinux on 2016-11-13
Just run into a similar problem upgrading from 15.10 to 16.10.
I've always managed to get the driver from [http://forschung.wi.uni-passau.de/~ond/hw/hanvon/](http://forschung.wi.uni-passau.de/~ond/hw/hanvon/) or  [http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/](http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/) to work though sometimes I'm not sure how.
After upgrading and installing the driver in my usual way...

cd /mnt/6f2d74b7-1d53-4d7b-a882-94217c5597ec/Downloads/hanwang/hanvon nov 2016
make
insmod hanvon.ko
mv ./hanvon.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet
depmod
# echo “hanvon” > /etc/modules

However now I get similar behavior to the other poster.
My usb mouse works ok but the tablet pen does not. As soon as I move the pen the cursor disappears, though objects on the screen react to the pens position ie tool tips and names when hovering over items. The pen buttons work and activate on screen buttons. As soon as I move the mouse the cursor re-appears.
Strangely when using GIMP (by the way why is this no longer in Ubuntu Software center) the behavior is different.
On opening Gimp and creating a new drawing the mouse moves the cursor until it enters the drawing area and the brush size appears. The brush icon moves over the image but the brush size indicator sticks at the edge and I can not paint. When using the tablet pen the brush cursor disappears but the brush size indicator moves across the page, though I can not paint.
This is where it gets complicated.
If I open configure input devices I see:
Core Pointer
Hanvon Artmaster I tablet
Logitech USB Receiver
Virtual core XTEST pointer
I can't remove any of these, though I'm sure I used to be able to.

With everything enabled ie set to screen mode the mouse operates normally and paints but the pen loses the cursor and will not paint.
                                    [TABLE]
[TR]
[TD="colspan: 4"]configure device state[/TD]
[TD="colspan: 3"]usb mouse[/TD]
[TD="colspan: 3"]tablet pen[/TD]
[/TR]
[TR]
[TD="align: left"]Core pointer[/TD]
[TD="align: left"]Tablet Pen[/TD]
[TD="align: left"]USB mouse[/TD]
[TD="align: left"]Vitual pointer[/TD]
[TD="align: left"]cursor[/TD]
[TD="align: left"]paints[/TD]
[TD="align: left"]brush size[/TD]
[TD="align: left"]cursor[/TD]
[TD="align: left"]paints[/TD]
[TD="align: left"]brush size[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"]screen[/TD]
[TD="align: left"]screen[/TD]
[TD="align: left"]screen[/TD]
[TD="align: left"]screen[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]yes[/TD]
[/TR]
[TR]
[TD="align: left"]screen[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]yes[/TD]
[/TR]
[TR]
[TD="align: left"]screen[/TD]
[TD="align: left"]screen[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]yes[/TD]
[/TR]
[TR]
[TD="align: left"]screen[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]screen[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[/TR]
[TR]
[TD="align: left"]screen[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]disabled[/TD]
[TD="align: left"]screen[/TD]
[TD="align: left"]yes[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[TD="align: left"]no[/TD]
[/TR]
[/TABLE]
    
My guess is that the mouse and tablet are interfeering somewhere though unplugging the mouse does not remedy the problem.
Any thoughts?

---

### Post by dmkonlinux on 2016-11-13
Just to add, when I disabled the features of the tablet pen one by one in gimps configure input devices it seemed that it was the pressure sensitivity that was causing the problem behaving as everything but the core pointer was disabled ie with the pen I could not see a cursor but could move the brush over the image and paint whereas with the usb mouse I could operate normally.
Don't know if this helps but I'll keep on playing.
Other people seem to be having problems with 16.10 and tablet pen pressure see [http://askubuntu.com/questions/840262/problem-with-old-genius-digital-drawing-tablet-ubuntu-16-10](http://askubuntu.com/questions/840262/problem-with-old-genius-digital-drawing-tablet-ubuntu-16-10) and also as a launchpad bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1639337](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1639337) , does this mean I have two issues to deal with ie pen pressure and disappearing cursor or are they the same?
I'm looking towards xorg [https://www.x.org/archive/X11R7.7/doc/man/man5/xorg.conf.5.xhtml](https://www.x.org/archive/X11R7.7/doc/man/man5/xorg.conf.5.xhtml) if it is some sort of problem between the mouse and graphics tablet but getting really tangled up and lost.

---

### Post by dmkonlinux on 2016-11-19
Well, I tried the remedy suggested here [https://bugs.freedesktop.org/show_bug.cgi?id=98575](https://bugs.freedesktop.org/show_bug.cgi?id=98575) which seems to have given me pressure sensitivity.
Having downloaded the correct version of xserver-xorg-input-evdev (This package provides the driver for input devices using evdev, the Linux kernel's event delivery mechanism.  This driver allows for multiple keyboards and mice to be treated as separate input devices) from [https://packages.debian.org/search?keywords=xserver-xorg-input-evdev, ]("https://packages.debian.org/search?keywords=xserver-xorg-input-evdev") I installed with gdebi which I had to download.
This has given me pressure sensitivity but not my cursor. Seems as though it is two problems.

---

### Post by dmkonlinux on 2017-02-12
It's been hectic so I have not made any time for this till now but this thread on askubuntu [http://askubuntu.com/questions/780027/ubuntu-16-04-hides-cursor-when-using-graphics-tablet](http://askubuntu.com/questions/780027/ubuntu-16-04-hides-cursor-when-using-graphics-tablet) is relevant.
The sugestion:
  gsettings set org.gnome.settings-daemon.plugins.cursor active true
  gsettings set org.gnome.settings-daemon.plugins.cursor active false

works as long as the mouse is not touched and the stylus is active ie on or near the tablet when the commands are entered into a terminal. Somewhat differently, my mouse, keyboard and tablet are all USB devices.
With further playing around I've discovered that the tablet and driver work as normal on a laptop running Lubuntu 16.10.
Other users [https://ubuntuforums.org/showthread.php?t=2339945](https://ubuntuforums.org/showthread.php?t=2339945) have reported similar situations with the tablet working in Ubuntu Mate 16.04.

---

### Post by dmkonlinux on 2017-02-12
Further along in the askubuntu post [http://askubuntu.com/questions/780027/ubuntu-16-04-hides-cursor-when-using-graphics-tablet](http://askubuntu.com/questions/780027/ubuntu-16-04-hides-cursor-when-using-graphics-tablet) Amias suggests using

 Option "HWcursor"

I had to create the file /etc/X11/xorg.conf (as Ubuntu no longer uses it) by copying a file made on my desktop with gedit using sudo cp 'source' 'destination'
 This seems to work though on restart the OS asked my if I wanted to use the default graphical settings which I accepted.

Strangely

Option "SWcursor"

Also works.

As an experiment I tried leaving an empty xorg.conf in the /etc/X11 folder and it still works!!!!!!!  Just checked and Lubuntu doesn't use /etc/X11/xorg.conf either but the tablet works??????

In all three cases I'm getting system problems detected though I can't say if these changes are the reason.

---

### Post by dmkonlinux on 2017-02-12
One more thing, the driver might not be actively maintained (I couldn't contact ondra.havel who has previously helped me). Another version based on this driver exists at [https://github.com/otakuchiyan/pentagram_virtuoso_drivers](https://github.com/otakuchiyan/pentagram_virtuoso_drivers) and may be newer although the version number is lower (4 versus 6), as does the Bosto tablets driver under development here [http://forum.bosto.co/](http://forum.bosto.co/).
To update I've found more sites
last updated in 2014 [https://github.com/exaroth/pentagram_virtuoso_drivers/blob/master/hanvon.c](https://github.com/exaroth/pentagram_virtuoso_drivers/blob/master/hanvon.c)
 last updated in 2015 [https://github.com/ondrah/hanvon](https://github.com/ondrah/hanvon)
last updated in 2016 [https://github.com/lbattraw/hanvon-linux/blob/master/hanvon.c]("https://github.com/lbattraw/hanvon-linux")
last updated in 2017 [https://github.com/uplusplus/hanvon-linux](https://github.com/uplusplus/hanvon-linux)

These all appear to be derived from [https://github.com/torvalds/linux/blob/master/drivers/input/tablet/hanwang.c](https://github.com/torvalds/linux/blob/master/drivers/input/tablet/hanwang.c) which was submitted to linux by a Hanvon / Hanwang employee in 2010 and I think explains why the hanwang module automatically loads when the tablet is activated but the tablet itself doesn't work as the models id's are different.

---

