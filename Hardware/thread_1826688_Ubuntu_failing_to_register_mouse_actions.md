---
title: "Ubuntu failing to register mouse actions"
date: 2011-08-16
forum: Hardware
---

### Post by Mr. Icarus on 2011-08-16
I recently set up a dual-boot of Windows 7 and Ubuntu 11.04 on my HP HDX 16 laptop.  Windows works fine, but while I am in Ubuntu the mouse will randomly stop registering any clicks at all on the system.  Windows are fine, the mouse still moves, and it is possible to navigate using the keyboard, but the system isn't registering any clicks at all, no matter which of my three mice (including built-in touchpad) I use.

The problem occurs even more often when I install and use the nVidia private drivers (both 173 and current version), and is crippling when I try to hook up another monitor.  Even after re-installing ubuntu on it's partition (10.04 LTS this time) the problem remained exactly the same. 

Has anyone else had a problem with this, or does anyone know what might be causing it?  I feel like it is a compatibility problem with the nVidia GPU, but I can't find specific errors, and the problem has not been reproducible in any way.

Any help at all would me massively appreciated, as I would really like to have ubuntu on my main machine.

---

### Post by Mr. Icarus on 2011-08-21
I got no responses on this, and I'm glad, since it was a noob question, and quite possibly troll-ish and un-answerable.  

I have found the problem and fixed it, and surprise, it had nothing to do with the nVidia card or drivers.

For any of you who run two (or more) different mice off of a single usb-port by utilizing a usb-expander - in my case my trackball and the gaming mouse I use on windows - **unplug the mouse you are not using.**  I am not sure what exactly causes ubuntu to freak out in that particular case, and it doesn't show up in error reports or traces, but the solution is simple.  Unplug the other mouse.

I don't feel that this necessarily warrants a bug-fix since it is so easily worked around, but someone may have greater inconvenience in disconnecting and reconnecting hardware all the time than I do.

Thanks, and I hope this helps anyone who may be experiencing the same problem.

---

