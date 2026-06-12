---
title: "Touchpad sensitivity"
date: 2013-05-31
forum: Hardware
---

### Post by AsusLappy on 2013-05-31
Context: Ubuntu 13.04 on an Asus UX31A

Almost everything works perfectly.... except for the touchpad. When I do a two finger tap (for right click) and sometimes the single tap (left click), it takes like 5 taps because I have to tap it "just right". Also it tends to drag things around the screen because it thinks I double tapped it while just navigating(so it's too sensitive in that case?). It's barely tolerable coming from the fantastic windows touchpad drivers for this laptop.

So is there a sensitivity setting I can change in some config file? A better driver I can install (i'm using the default ubuntu one)?

---

### Post by ohnonot on 2013-06-01
i've had similar problems and used settings from this [archwiki article]("https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Frequently_used_options"); it works on other distros, on ubuntu too, iirc.

---

### Post by AsusLappy on 2013-06-03
I don't have Xorg.conf.d or 50-synaptics.conf or whatever :/

---

### Post by ohnonot on 2013-06-04
i just booted into my ubuntu install to see what is happening here. you are right. but now i found it:
open a terminal, type
```
synclient -l
```
and have a good look.
then type
```
man synclient
```
- it says var=value midway through; that should give you an idea what kind of command you need to use to set it up properly.
you can chain the options, like 'synclient var1=value var2=othervalue ....'
i say the archwiki article will still be very helpful with finding sane defaults - which is what you are asking for, basically.
if you found your favorite settings, create an autostart entry that executes that every time you log in (type startup in dash).
setting up a touchpad is a very individual thing, and you will have to go through some configuration yourself.
this might also be of interest to you:
```
man syndaemon
```

---

