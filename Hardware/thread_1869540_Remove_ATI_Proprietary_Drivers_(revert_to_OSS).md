---
title: "Remove ATI Proprietary Drivers (revert to OSS)?"
date: 2011-10-25
forum: Hardware
---

### Post by SPARTAN-118 on 2011-10-25
Using Ubuntu 11.10 "Can't-even-begin-to-pronounce-it Ocelot"

Hi, I recently installed GNOME-shell from Ubuntu Software Center in the hopes that I could get away from Unity, which is stupidly slow on my system (Athlon 64 3200+, 2GB DDR2 RAM, and ATi HD Radeon 3650).

However, upon starting up my new GNOME 3 environment, I couldn't help but notice that all the menus, including the panel up top, are unreadable.

Screenie:

[[IMG]http://i41.tinypic.com/288txqw.png[/IMG]](http://i42.tinypic.com/fxzfcz.jpg)

I have a feeling this is due to the fglrx drivers. This may seem like a newbish question, but how do you revert to the Open Source drivers? I'm presuming you uninstall the package, then restart, and I'm pretty sure I've done it before, but I don't remember *how*.

Help?

---

### Post by Redblade20XX on 2011-10-26
Take a look at this:
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

:)

- Red

---

### Post by SPARTAN-118 on 2011-10-27
What the heck?? I could have sworn I posted a new reply!

Anyway, I *thought* I had posted the code for the Terminal output a few days ago, but I guess not. That really sucks, because it would have probably helped soo much...

Anyway, I'm not sure if I successfully managed to uninstall the fglrx drivers. I don't think I did, because when I tried the commands on the page you linked to, and on the Ubuntu Wiki page *that* page linked to, the Terminal gave me an error. 

Now, when I boot into GNOME, it automatically reverts to GNOME Classic, even if that's not what I intended to log into. This is what my desktop now looks like:

EDIT: YES!!! Finally got everything working properly! :D

That page you linked to? I followed these steps:

```
$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo rm -rf /etc/ati
```

Should have done that ***first***; instead, I ended up doing them ***last***!

No matter. I think you get how happy I am.

This is what my desktop now looks like, thanks to you:

[[IMG]http://img831.imageshack.us/img831/7383/screenshotat20111027162.png[/IMG]](http://imageshack.us/photo/my-images/831/screenshotat20111027162.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by philipobrien on 2011-11-06
Hello, I have a notebook, dm3-1030us with ATI HD 3200, the procedure used on the link below to install my video card, but I'm having some problems with some images and menus that are in the distorted image.

 you had this problem too?

 following picture of my screen bugged

[IMG]http://imageshack.us/photo/my-images/217/capturadetelaem20111106.png/[/IMG][http://imageshack.us/photo/my-images/217/capturadetelaem20111106.png/](http://imageshack.us/photo/my-images/217/capturadetelaem20111106.png/)
[IMG]http://imageshack.us/photo/my-images/217/capturadetelaem20111106.png/[/IMG]

---

### Post by SPARTAN-118 on 2011-11-06
That's not *quite* the same problem I had. Actually, that would look pretty cool, if it didn't prevent you from using some programs.

Do you know if you are using the fglrx (Proprietary ATi) drivers or the open source ones?

If you're using the Proprietary drivers, you should have the AMD/ATi Catalyst Control Center installed somewhere on your system. If you did not activate any drivers in the "Additional Drivers..." application, and CCC is not anywhere on your system, chances are you're using the open source drivers.

---

### Post by xm4ss4cr3 on 2011-11-10
I've been using Ubuntu for about 4 years now, and it keeps amazing me all the tricks you have to perform to get your hardware working (logitech marblemouse, ati radeons, even the cpu-cooling in my t500...).

But that's not the point now. I followed everything in the how-to at [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide), but I still have a few small things:

[LIST]
[*]in alt-boxes and dropdown menu's under boxes with search history there still is some tearing
[*]under system settings -> system info -> graphics it still says Driver: VESA: M86
[*]the occasional semi-crash/restart of gnome3 restarting with my windows still open (think it's a driver issue)
[/LIST]

does anyone else have any of these problems or fixes for them?

hardware:
lenovo thinkpad t500, radeon hd 3650

edit:
it's sort of like what philipobrien is experiencing, but only in alt-boxes/autofill menu's...

---

### Post by SPARTAN-118 on 2011-11-10
I just did some quick research, and it appears that VESA is a default, or failsafe, driver.

Have you tried looking in "Additional Drivers" for the proprietary ATi ones? I realize that I said the fglrx drivers were causing issues for me, but if you're using the VESA drivers...

or have you tried the AMD/ATi ones already?

---

### Post by xm4ss4cr3 on 2011-11-11
I tried fglrxinfo
```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3650
OpenGL version string: 3.3.11161 Compatibility Profile Context

```

and even fgl_glxgears works...

even compiz and all the fancy visual things in gnome3 work, could it be that the systeminfo is displaying the wrong info?

---

### Post by SPARTAN-118 on 2011-11-12
Yeah, that is weird.

Unfortunately, I'm no Linux expert. (In fact, I'm actually using Vista ATM.)

So, looks like we'll just have to either wait for someone who *is, *or you'll have to do some research for yourself. (Just use Google and search for different variations of what you're experiencing, that's usually what I do while waiting for a reply.)

I would strongly suggest that you create your own thread, as this one is marked as SOLVED and is only related to your problem by a stretch.

---

### Post by xm4ss4cr3 on 2011-11-14
Everything seems to work fine, the crashes just stopped happening after some fiddling and the alt-boxes being distorted I can live with.

Guess I'll just wait for an updated driver and perform a reinstall when they get released. In the meantime I can work on making ubuntu behave like I want it, and IF I happen to f..k something up it's "Meh, reinstall it..." :P

---

