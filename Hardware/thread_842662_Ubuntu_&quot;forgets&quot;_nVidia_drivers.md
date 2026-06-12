---
title: "Ubuntu &quot;forgets&quot; nVidia drivers"
date: 2008-06-27
forum: Hardware
---

### Post by sideburns on 2008-06-27
My sister uses Ubuntu and I'm her in-house tech support.  She has a GeoForce video card, and the drivers were working just fine.  "Were" being the operative word here.  This morning she tried to open Google Earth and itt complained that it didn't know what her video car was.  Checking, I could find no evidence that the proper drivers were loaded.  (dmesg | grep -i nvidia produced no results)  I checked with Hardware Drivers and it said the drivers were present and enabled.  The nVidia Display Settings tool told me that the drivers weren't configured and to use nvidia-xconfig as root.  Alas, the program was not found.  Checking, there is no such file on her computer.  I tried rebooting.  Now, there's mention in dmesg of the drivers being loaded, but Google Earth still can't find them and the Display Settings tool won't work.  Does anybody know what might have happened and/or how to fix it?

---

### Post by starcannon on 2008-06-27
Alt-F2

```
gksudo gedit /etc/modules
```

add the word
```
nvidia
```
to the list.

reboot, that may fix it for you, I install my drivers manually and this is one of the steps I have to do in order for Ubuntu to "remember" my video card.

GL

---

### Post by sideburns on 2008-06-27
Thank you for your fast response.  Alas, there was no change when I rebooted.

---

### Post by starcannon on 2008-06-27
sideburns if your up for a manual install, I'll be around awhile to help, could even be convinced to remote desktop if you'd like, I use nvidia cards as much as possible because they work so well, and *breaks own arm* i've gotten quite good at installing them.

I wrote a guide here:

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

Let me know how your getting along, and what help you need, glad to be of service.

GL

---

### Post by sideburns on 2008-06-27
I would only consider that if I were desperate, and I'm not, at least not yet.  When we installed Ubuntu, it claimed tot install the right drivers.  It claims to have them enabled.  They just don't seem to work correctly.  I'm going to try disabling them, then re-enabling them and see if that gets things properly installed.  KISS time.

---

### Post by sdennie on 2008-06-27
How did you initially install the drivers?  There was an update to xserver-xorg-core recently and that would have blasted the opengl functionality of the nvidia card so you'd have to re-install the drivers if you installed them manually (not sure if you used EnvyNG).

---

### Post by starcannon on 2008-06-27
Cool let us know if you meet success. And what steps you used.

---

### Post by sideburns on 2008-06-27
Disabling, re-enabling and restarting didn't help.  I tried installing nvidia-xconfig and using it, but that didn't help.  All I got was a warning at boot that it didn't know what video card or monitor we were using, and I had to figure out what the magic combination was.  Alas, we were still stuck in 800x600 mode.  (We've been there before, so I was familiar with it.)  Checking, it now claimed that the nVidia drivers weren't enabled, so I enabled them AGAIN and rebooted.  This time it worked.  I have no idea what was wrong, or why disabling and re-enabling them worked the second time but not the first.  This is NOT the way Ubuntu, or any other distro is supposed to work.

I guess this just proves that Ubuntu nas a positive Lovelace[1] value, even though it's far, far smaller than anything from the Dark Lord of Redmond.  I'm not surprised; I doubt a Ll of 0 is possible, even in theory.

[1]The standard unit of suckiness is the Lovelace (Ll).
This is defined as:  One Lovelace is the amount of force (measured in dynes) it takes to draw a round ball weighing e Troy Ounces down a tube it fits exactly (in air) at a speed of pi attoparsecs/microfortnight.

Like Farads, this is a rather large measurement.  Thus, Plan 9 sucks a few
mLl, for instance, while your average Microsoft product achieves many Ll.

---

### Post by sideburns on 2008-06-27
> **vor said:**
> How did you initially install the drivers?  There was an update to xserver-xorg-core recently and that would have blasted the opengl functionality of the nvidia card so you'd have to re-install the drivers if you installed them manually (not sure if you used EnvyNG).
When we first installed, Ubuntu claimed to pick up the right drivers automagically, but somehow, things were never right.  Enby didn't help.  It turned out to be a combination of enabling the drivers and making sure the right monitor was selected, to give us access to the right resolution and refresh rate.

---

