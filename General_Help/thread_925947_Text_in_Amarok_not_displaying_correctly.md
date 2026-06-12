---
title: "Text in Amarok not displaying correctly"
date: 2008-09-21
forum: General Help
---

### Post by ztirffritz on 2008-09-21
When I open Amarok, all of the text is missing.  There is often a single dash (-) in place of the text.  If I expand a section it will sometimes show some text for a bit, then it goes away again.  Anyone know how to fix this?  It makes using Amarok very difficult.  I'm using Ubuntu 8.04 (Hardy) on a x386.

---

### Post by stoumpos on 2008-11-06
I have the same problem. In some cases, clicking on a widget
will redraw some elements correclty, but the user interface
is completey unsusable. I am using Ubuntu 8.10.

---

### Post by ztirffritz on 2008-11-06
I found that if I changed the resolution in he nvidia settings screen it would fix the problem temporarily. Even if I set it to the current resolution. Try that.

---

### Post by stoumpos on 2008-11-12
That didn't help in my case because the nvidia settings do
not allow me to change the screen resolution. It seems that
kde packages that depend on kde4 libs are ok. The problem
with amarok might originate from the dependency to kdelibs4c2a.

---

### Post by Jeffa on 2008-11-12
I'm having the same problem. There's a screen grab here:

[http://ubuntuforums.org/showthread.php?p=6157407#post6157407](http://ubuntuforums.org/showthread.php?p=6157407#post6157407)

Since I've also had problems in another program, I'm wondering if it isn't a nvidia driver issue. What GPU chipset are you using? If you have a Nvidia card, are you using their proprietary drivers or the open source NV driver?

---

### Post by stoumpos on 2008-11-16
My graphics card is (according to lspci):
01:00.0 VGA compatible controller: nVidia Corporation
NV34 [GeForce FX 5200] (rev a1)

I am using "version 96" nvidia driver, because the newer
versions produce artifacts when rendering the titlebars.
I am also using a second computer with a GeForce 8400
that does not have this problem.

---

### Post by upallnight on 2008-11-21
Same problem here with Amarok menus and text blank.

When I click on a menu, the text is visible for about a fourth a second then it disappears.

I am running the Nvidia GeForce4 420 Go 32M video card using the Nvidia Accelerated Graphics Driver version 96 from the Hardware Drivers tool and Intrepid 8.10 with Visual Effects set to Normal.

When I set Visual Effects in the Appearance tool to "None" the problem goes away... but i like the visual effects :(

---

### Post by sender on 2008-11-21
Hi

I've got the same problem with my GeForce 420go 16mb

Switching off visual effects did work for my, but like upallnight I would be very happy if I was able to run them

---

### Post by Elfy on 2008-11-21
check which version of the driver you are using = 96.43.05 is a problem

---

### Post by sender on 2008-11-21
> **forestpixie said:**
> check which version of the driver you are using = 96.43.05 is a problem

96.43.09

---

### Post by Elfy on 2008-11-21
that one should work - did you get it from proposed updates or nvidia?

---

### Post by sender on 2008-11-21
> **forestpixie said:**
> that one should work - did you get it from proposed updates or nvidia?

proposed updates

---

### Post by Elfy on 2008-11-21
Might be worth a dig around on the nvidia forums - I had a problem with the fonts looking like someone had scribbled them out with my GeForce4 - could be tied up with text antialiasing.

The problems I was getting disappeared with a clean install - previously I was running an install that had started with the pre alpha intrepid and had all sorts done to it - maybe there was soemthing in my /hopme causing the problem? I'm not suggesting you reinstall though - just a bit of background.

[This]("http://ubuntuforums.org/showpost.php?p=6211952&postcount=14") post from this [thread]("http://ubuntuforums.org/showthread.php?t=986818") might be of use

---

### Post by sender on 2008-11-22
Ok I found solution for this problem here [Click]("http://www.nvnews.net/vbulletin/showthread.php?p=1838646#post1838646")

All I had to do, was edit xorg.conf file and add this:
```
Option "RenderAccel" "0"
```
in "Device" section

and now everything works fine for me :)

---

### Post by upallnight on 2008-11-22
> **sender said:**
> Ok I found solution for this problem here [Click]("http://www.nvnews.net/vbulletin/showthread.php?p=1838646#post1838646")

All I had to do, was edit xorg.conf file and add this:
```
Option "RenderAccel" "0"
```
in "Device" section

and now everything works fine for me :)

Works for me too! Thanks :)

---

### Post by sender on 2008-11-22
Can someone change thread title, and mark it as solved ??

---

### Post by upallnight on 2008-11-23
One strange thing I've noticed after adding the RenderAccel option is the Theme turns blue and blocky about every 20 minutes. Starting the Appearance Preferences tool changes the Theme back to normal.

The reason the Theme is being reverted is because the gnome-settings-daemon is crashing. Running gnome-settings-daemon in a terminal restores the normal Theme and starting Appearance Prefs tool must start the gnome-settings-daemon.

Seems setting the RenderAccel option to 1 doesn't keep gnome-settings-daemon from crashing so this must not be related to the graphics card.

---

### Post by SocratesTNR on 2008-11-24
Option "RenderAccel" "0" didn't work for me, or a lot of other people.


[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836)

[http://ubuntuforums.org/showthread.php?t=991274&goto=newpost](http://ubuntuforums.org/showthread.php?t=991274&goto=newpost)

Driver 96.43.09 is a problem as well...

There's stuff about this all over the net...

You are not alone.

I suggest we all gang up and mosey on over to the NVIDIA forums ad complain...

---

### Post by stoumpos on 2008-11-25
I finally upgraded the nvidia drivers to version 173
and text is properly displayed. However, artifacts
appear on the titlebars (see [http://ubuntuforums.org/showthread.php?t=970954](http://ubuntuforums.org/showthread.php?t=970954) for more details).

---

