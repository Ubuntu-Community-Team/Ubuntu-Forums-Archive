---
title: "ATI on Edgy"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by SteinbergerNate on 2006-12-14
Not sure if anyone has figured this out yet. I'm still on Dapper and would like to go to Edgy but would like to see if anyone knows if the horrible problems with the fglrx driver on Dapper still exist in Edgy. It's on a Dell 600m laptop. Sorry I can't tell you what the model is on the chipset. I don't have the machine here in front of me.

---

### Post by raul_ on 2006-12-14
I have an ATI and i'm even running Beryl =) fast as bullet.
```

raul@raul:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

---

### Post by SteinbergerNate on 2006-12-14
So, you didn't have to do any of the weird tricks everyone was pulling out in Dapper to get that working? Oh, I do hope that the issue is resolved in Edgy. That would make everything just peachy :)

---

### Post by raul_ on 2006-12-14
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Check this link. I followed the first link and i had no problems

---

### Post by drphilngood on 2006-12-14
Here´s another good guide:

[BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Good luck!

---

### Post by kmellos on 2006-12-17
> **raul_ said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Check this link. I followed the first link and i had no problems

Can you please give me the guide that helped you install Beryl?

I tried but end up with this error:

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

---

### Post by Adapted.Cat on 2006-12-17
> **SteinbergerNate said:**
> Not sure if anyone has figured this out yet. I'm still on Dapper and would like to go to Edgy but would like to see if anyone knows if the horrible problems with the fglrx driver on Dapper still exist in Edgy.

They definitely do. If you had horrible problems in Dapper, then you will probably have horrible problems in Edgy. If you didn't...well, good luck with that. The good news is that the generic 'ati' driver now claims to support acceleration for up to R300 chipsets (however I have an R200 chipset and can not get direct rendering to work). The bad news is that the latest ATI fglrx drivers only support R300 and up. The fglrx included in Edgy is not quite the latest, so it may work with your machine.

To figure out which you have, run X with the 'ati' driver and look through /var/log/Xorg.0.log
Then look up the result here: [http://dri.freedesktop.org/wiki/ATIRadeon]("http://dri.freedesktop.org/wiki/ATIRadeon")

It took me weeks to fix up Dapper, and my initial attempts to get direct rendering in Edgy failed, so I've dropped back to the generic ati driver. I do at least get crash-free 2D graphics, so long as I stay away from glxinfo/glxgears.

A quick scan of the forums indicates that I'm not the only one. ](*,) 

Rather than waste more weeks of my life trying to get it working, I was thinking of getting an NVIDIA card, if I can ever figure out their product numbering scheme. Not very helpful for you, I know - sorry :(

PS: Remember - Alt+SysRq + [R, S, E, I, U, B] in that order should reboot you cleanly.

---

### Post by mattyranks on 2006-12-17
I have to say that compared to dapper, edgy does a better job with ATI cards

if you follow the [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) guide you should get the ATI drivers installed relativley easy.

---

### Post by eye208 on 2006-12-18
> **SteinbergerNate said:**
> I'm still on Dapper and would like to go to Edgy but would like to see if anyone knows if the horrible problems with the fglrx driver on Dapper still exist in Edgy.

You can test it for yourself using the Edgy Live DVD (or the CD if you have a working internet connection):

Press F6 at the Live DVD boot screen, then replace the parameter "splash" with "single" and press Enter. This will boot the DVD into single user mode ("root@ubuntu:~#"). Enter the following commands:

# cd /etc/rc2.d
# mv S13gdm K87gdm
(if it's a Kubuntu disc, enter "mv S13kdm K87kdm" instead)
# telinit 2 ; exit

Now you're in multiuser command line mode ("ubuntu@ubuntu:~$"). Proceed as follows:

$ sudo apt-get update
$ sudo apt-get install xorg-driver-fglrx
$ sudoedit /etc/default/linux-restricted-modules-common
(remove fglrx from the list of disabled modules and save the file)
$ sudo /etc/init.d/linux-restricted-modules-common start
$ sudo aticonfig --initial --ovt Xv
$ sudoedit /etc/X11/xorg.conf

Add these lines to xorg.conf:

Section "Extensions"
Option "NoComposite"
EndSection

Look for the device section containing the string:

Driver "fglrx"

Add this line (laptops only):

Option "MonitorLayout" "LVDS"

Save the changes. Now you can load the graphical desktop by entering:

$ startx

If you decide to install Edgy, remember to install linux-restricted-modules as well. In the file "/etc/gdm/gdm.conf" (Kubuntu: "/etc/kde3/kdm/kdmrc") look for the option "AlwaysRestartServer" (Kubuntu: "TerminateServer"), remove the comment sign (#) and set the option to "true". This will prevent X.org from crashing on session logout.

---

### Post by Adapted.Cat on 2006-12-19
> **eye208 said:**
> You can test it for yourself using the Edgy Live DVD (or the CD if you have a working internet connection):

I tried this, using exactly your instructions, and got the same results as I had before. The X server starts, and everything seems fine, but the first access to accelerated graphics (even a fglrxinfo) causes the machine to lock up. Mine's a "ATI Technologies Inc Radeon R200 QM [Radeon 9100]"

At least I know it's not just my installation that's the problem.

Has anyone had luck getting accelerated graphics from the open source driver?

---

### Post by SteinbergerNate on 2007-01-13
Oh, how I wish it were just as simple as going to synaptic or easyubuntu and selecting the ati driver.

---

