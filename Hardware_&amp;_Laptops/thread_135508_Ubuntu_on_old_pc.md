---
title: "Ubuntu on old pc"
date: 2006-02-24
forum: Hardware &amp; Laptops
---

### Post by balaji on 2006-02-24
Hi

I've installed ubuntu breezy on an old pc - P3 750 MHz, 128 MB RAM, 20 GB HD. everything is pretty slow now. I read that gnome takes up a lot of ram - so what window manager can I use as an alternative (I'm a newbie, so I'd be grateful if you could give detailed information). Also can I do anything else to make it run faster?

Thank you
Balaji

---

### Post by sabredog on 2006-02-24
Personally I would install XFCE. This is a nice lightweight DM that does not chew up RAM as Gnome and KDE do.

[http://www.xfce.org/](http://www.xfce.org/)

Xubuntu offers a lightweight Ubuntu based distro with XFCE as a DM.

---

### Post by az on 2006-02-24
1.  If you can, buy more ram.
2.  Install icewm.

Enable the universe repository, update and install icewm and menu.  Log out of gnome and change your session to icewm and log back in.  Blink and you are at the desktop.

You can install rox-filer and run it with the -p=1 option to give yourself a desktop that you can put files onto.

---

### Post by balaji on 2006-02-24
Thank you Sabredog - I am using Xubuntu now and its definitely faster.

Azz
Are iceWM and rox-filer two alternatives? Or should I install rox-filer after installing iceWM? Also, could you give me the full run command for rox-filer? I'm a newbie, so please bear with me.

Thank you
Balaji

---

### Post by mjwood0 on 2006-02-24
I'm using Xubuntu on an old PII 333 w/ ~192MB RAM and it runs pretty good.  Granted it takes a while to boot, but hey -- its functional.  

Mostly, this PC is my server so I rarely have occasion to go into any graphical display, but it's nice to have there if I ever want to do something with it.

---

### Post by az on 2006-02-24
[QUOTE=balaji]
Azz
Are iceWM and rox-filer two alternatives? Or should I install rox-filer after installing iceWM? Also, could you give me the full run command for rox-filer? I'm a newbie, so please bear with me.

Thank you
Balaji[/QUOTE]
Icewm is a display manager.  It displays a background, and drawn the windows on it, but you cannot use the background as a file manager.

Rox is a file manager.  You can run it in any environment.  You can tell it to create a desktop (pinboard)

rox -p=1

---

### Post by cotcot on 2006-02-24
As azz says more ram is usefull. My PC 2 (see signature) runs in an acceptable way also for graphics (gimp, video). I bought the extra ram on internet second hand site.

---

