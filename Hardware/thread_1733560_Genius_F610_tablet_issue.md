---
title: "Genius F610 tablet issue"
date: 2011-04-19
forum: Hardware
---

### Post by josempans on 2011-04-19
I was reading a lot of thread about this subject... My Tablet works, and it's recognized by ubuntu... but with very weird and annoying issues... Ubuntu don't recognize the "over tablet" movement... only when I put the pencil on the tablet, and it acts like a left click, so when I drag the pointer draws the selection box.
Looks like Ubuntu don't see when I move the pen without touching the tablet.. In windows works perfectly (but i want to leave windows!!)

What can be the problem... I've tried all things in the threads... also there is a blog post about this, and talks about "sudo /etc/rc.something start" well, that command says that there is no UDev tablet... so something is not working properly i guess...

Thanks a lot in advance!

---

### Post by Favux on 2011-04-19
Hi josempans,

You don't say which release of Ubuntu you are using.

Anyway I think you have a rebranded Waltop tablet.  Enter *lsusb* or *xinput list* in a terminal to check.

If so see the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

My guess is your current problems are because the tablet is on the evdev X driver.

---

### Post by josempans on 2011-04-19
oh, :P.. I forgot to mention the version... Ubuntu 10.04. I'll do that and let you know... thanks!

---

### Post by josempans on 2011-04-19
ok... I'm near to quit, :P... too many information and i don't know what to do
this is my xinput info:

> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet      id=8    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

The tablet buttons don't work  well, there is no "translation" over the tablet, sometimes yes, sometimes no... sometimes the pen tip acts well, and sometimes work only like left click.
I've tried uninstalling the wizardpen driver to have no conflicts with wacom... I don't know if uninstalling wacom drivers and re-installing wizardpen will work. When I want to try to uninstall the wacom ubuntu shows me that it will uninstall another package too (xorg-*-all) is this ok?

---

### Post by josempans on 2011-04-19
OMG is working!!... thanks!!!

For anyone with the problem: for Genius F610 tablet in a Ubuntu 10.04
Just follow this:

[http://ubuntuforums.org/showpost.php?p=9966110&postcount=1](http://ubuntuforums.org/showpost.php?p=9966110&postcount=1)

Thanks FAVUX!!

---

