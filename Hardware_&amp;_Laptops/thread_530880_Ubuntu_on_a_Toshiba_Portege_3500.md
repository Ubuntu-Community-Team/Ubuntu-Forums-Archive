---
title: "Ubuntu on a Toshiba Portege 3500"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by nlemay1 on 2007-08-20
I'm a computer repair tech and I've just started installing Ubuntu on all of the servers and systems at my work, but I've never had to configure Ubuntu for a tablet PC. I'm buying a Portege tomorrow and i would MUCH rather have Linux running on it than Windows. I know that this brings up some problems considering there isn't necessarily a Ubuntu Table Edition or anything (that I know of) and also some configuration settings that I am not aware of. If someone could give me sort of a tutorial on how I would do this, it would be much appreciated. Thanks.

---

### Post by miatared on 2007-11-06
Too bad you did not get an answer - I have a 3500 also and am looking at installing Ubuntu 7.10... 

I have the Targus Noteworthy external CD and it will not install, I get a prompt and do not know what to do next ???

MiataRed

---

### Post by captainwitherspoon on 2007-11-07
same here, can anyone help?

---

### Post by xzero1 on 2007-11-09
After a Gusty upgrade from Feisty.
Screen will not rotate.:(
Stylus works but no buttons*

Tickless kernel is NICE.:)
Wireless works fine, Feisty had issues.
Audio works fine.
Will suspend but screen will not wake up.*
Hibernate did seem to work (tried once).
Could not install Feisty from cd but used a netboot install. Gusty was installed from within Feisty.
If dual booting WUBI might work but is in beta.
I suggest you install powertop for a few powersaving tweaks.
With 512M runs MUCH better than xp!:guitar:

*Update:
stylus right click works while stylus pressed down see:
[http://ubuntuforums.org/showthread.php?t=590747&highlight=stylus+button]("http://ubuntuforums.org/showthread.php?t=590747&highlight=stylus+button")
Suspend works with a new kernel 2.6.23.1 compile using the old slab allocator, but pen will freeze upon wakeup.

---

### Post by captainwitherspoon on 2007-12-09
How do you do a net-boot install? I can't install from the cd either...

---

### Post by captainwitherspoon on 2007-12-09
Oh yeah, does compiz work on the portege 3505? It seems like it wouldn't, how about that monitor port in the back, can you still run two monitors?
I would *love* running ubuntu on this computer if I can get most things to work.

---

### Post by xzero1 on 2007-12-10
> How do you do a net-boot install? I can't install from the cd either...

Sorry, I don't remember the details but this link should help.
[https://help.ubuntu.com/community/Installation/Netboot]("https://help.ubuntu.com/community/Installation/Netboot")
An easier way would be a wubi install. This is a program run from windows that installs a bootable ubuntu inside a windows file see [http://ubuntuforums.org/showthread.php?t=396526]("http://ubuntuforums.org/showthread.php?t=396526").

I have not tried an external monitor on this pc. Compiz does not work.
I have gotten suspend to ram to work although the pen functionality is lost when the pc wakes up.  I believe most of the issues can be fixed with a bit of time and effort.

---

