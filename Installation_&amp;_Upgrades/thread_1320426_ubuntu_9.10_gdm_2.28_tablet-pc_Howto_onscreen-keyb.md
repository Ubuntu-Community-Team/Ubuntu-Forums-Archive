---
title: "ubuntu 9.10 gdm 2.28 tablet-pc: Howto onscreen-keyboard for screen unlock password"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by 1wang on 2009-11-09
ubuntu 9.10 studio with gdm 2.28: Howto install onscreen-keyboard for screen unlock password for tablet-pc with touch-pad with digitizer-pen ?

I am using a IBM X41 tablet notebook

I installed the onboard onscreen-keyboard as well as the matchbox-keyboard

initial login from gdm with onboard works:
------------------------------------------------
For initial login from gdm I used the new access preferences on the bottom of the login gdm screen to switchh on the onscreen display and it works.

screen unlock with digitizer pen does not work:
------------------------------------------------------
After screen lock I can get the login screen by moving my digitizer pen but I could not find out how to configure an onscreen-keyboard here. 

In ubuntu 9.04 I used the mouse gesture as describe in [https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM](https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM) to get an onscreen keyboard for typing in the pasword in gdm. 

But in ubuntu 9.10 the file /etc/gdm/modules/AccessDwellMouseEvents and all the modules under /etc/gdm/modules do not exist any more. 

I  tried a configuration with the gconf-editor in the key directory /apps/gnome-screensaver as described in [http://wiki.linuxquestions.org/wiki/Tc1100:](http://wiki.linuxquestions.org/wiki/Tc1100:)

Inside that directory I turned on the boolean key embedded_keyboard_enabled.
I also change the value of the key embedded_keyboard_command 
I tried the matchbox-keyboard --xid as well as onboard there
But both did not work under ubuntu 9.10

need help !

thanks a lot

---

### Post by Favux on 2009-11-09
Hi 1wang,

I posted a mini HOW TO [here]("http://ubuntuforums.org/showpost.php?p=7959338&postcount=8").  The rest of the thread has some more information on it too.  One of the links on my post describes a screensaver keyboard widget which I didn't investigate.  I don't know how well all this would work in Karmic.

Hope this is of some help.

---

### Post by 1wang on 2009-11-25
still no solution but a suspicion

Many thanks for your reading hints. Some were new to me some I had read before. But none brought me a solution. 

1. approach using gestures does not work:
My suspicion is that it has to do with the gnome themes. In ubuntu 9.04 some setting like "no loginscreen theme" existed. And there was an inconsistency for the gesttik package with gnome-themes. This possibly makes the usage of gestures on gnome impossible. 

2. approach using gnome accesibility functions does not work either:
Use gconf-editor  goto directory /apps/gnome-screensaver and setup there an onscreen display with the keys: embedded_keyboard_enabled and embedded_keyboard_command as described in my last post in this thread does not work. Possibly this also has to do with the gnome themes, which can not be switched of ?

Might be worth to file a gnome accessibility bug ?

---

### Post by Favux on 2009-11-25
Hi 1wang,

> Might be worth to file a gnome accessibility bug?
That seems reasonable.  Slate style and tablet pc's should be supported too.

Speaking of gestures, have you looked at Tom Jaeger's EasyStroke?

[http://sourceforge.net/projects/easystroke/](http://sourceforge.net/projects/easystroke/)

[http://sourceforge.net/apps/trac/easystroke/wiki/Documentation](http://sourceforge.net/apps/trac/easystroke/wiki/Documentation)

[http://ubuntuforums.org/showthread.php?t=837032](http://ubuntuforums.org/showthread.php?t=837032)

---

### Post by tkdryan on 2010-01-30
I was wondering how to do this same thing, also using ubuntu 9.10. What I realized is that you can just press the switch user button at the locked sceen window which takes you back to a full login window, but doesn't log you out. From here you can just press on your username again and use the OSK like you would when you log in. Presto, now you can unlock your screen with 1 extra pen press.

Not that the root problem of no OSK @ the lock-out screen doesn't need to be fixed... Hope this helps someone out there.

(im using onboard by the way)

---

