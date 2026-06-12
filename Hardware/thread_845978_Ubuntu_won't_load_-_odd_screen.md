---
title: "Ubuntu won't load - odd screen"
date: 2008-07-01
forum: Hardware
---

### Post by Monsieur Williams on 2008-07-01
Recently I just tried to run the LiveCD of Ubuntu on my Toshiba P200 laptop and the resolution was detected successfully, however, when it came to loading past the splash screen, the screen kept blurring in and out, and then after, just odd pixels popping up and I had to resort to turning off my laptop. (I've tried running both the LiveCD and Wubi)

Does anyone know the cause or a resolution to this problem? :confused:

*Thanks!*

P.S - I'm a newbie to this stuff.

---

### Post by lisati on 2008-07-01
What sort of specs does your machine have? e.g. amount of RAM and that kind of stuff.

---

### Post by Monsieur Williams on 2008-07-01
Processor: Intel Core 2 Duo
Ram: 2GB
Graphics: ATI Mobility Radeon HD 2400
Sound: Realtek High Definition Audio
Hard Drive: Hitachi - 250GB
CD-ROM: Pioneer DVD-RW

Anything else? :)

---

### Post by Monsieur Williams on 2008-07-01
I've got some more information. After attempting to load Ubuntu without xorg.conf I found that a few messages popped up that stated a file or folder for ACPI was missing and of course, a message about the missing xorg.conf

---

### Post by Alexis Phoenix on 2008-07-01
I didn't know you could run a live cd version without xorg.conf!  Anyway, it could be that your cd, or the image used to create it, is slightly corrupted (this has happened to me, long ago).

You could also try to see if the laptop works with other distributions.

Alexis Phoenix

---

### Post by Monsieur Williams on 2008-07-01
I tested Fedora just recently from a DVD and it still produced a wierd screen.

---

### Post by Alexis Phoenix on 2009-06-07
I've been thinking about your problem, and this is what I thought.  It sounds like the driver used by xorg isn't behaving correctly.  You can set it up to use the vesa driver.  This is most basic driver and should work with any vesa compliant graphics card (pretty much all of the ones in current use).  Start it with xorg.conf enabled, but start it in failsafe mode - you should be able to use a console that way, open the nano text editor, open xorg.conf (type the following at the console) ```
nano /etc/X11/xorg.conf
``` and find the line that says ```
"driver"     "(something)"
``` and change (something) to vesa.  Save the file (ctrl-o) and exit (ctrl-x).  Start xorg by typing ```
startx
``` - hopefully you will now have a working gui and can go on to install with that version of the file.  The missing ACPI stuff is probably due to a bios bug, or something needs to be turned on in the kernel.  Possibly the installed version or it's updates will provide a fix for this, but I don't know anything about your laptop so can't really say.  Try [www.tuxmobil.org](www.tuxmobil.org) for a place to start looking for help.

I hope all goes well for you.
Cheers,
Alexis

---

