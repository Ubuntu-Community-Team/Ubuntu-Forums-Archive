---
title: "Can't get native screen resolution?"
date: 2008-07-31
forum: General Help
---

### Post by Wild Squid on 2008-07-31
How can I change my screen resolution if the screen resolution options show 800x600 as the max? When I reboot the screen is at a higher/native resolution, but once I'm logged in , it changes back to 800x600. I think I may have done something to it after I tried to run this: sudo gedit /etc/X11/gdm/gdm.conf I was trying to change Ubuntu's AllowRoot=false to AllowRoot=true. But nothing came up in the gedit scree, so I just closed it. Please help a newbie Linux user!

---

### Post by tuxxy on 2008-07-31
Did you install the drivers for your graphics card, if so what montior are you using

---

### Post by Wild Squid on 2008-08-01
Well, don't have a video card, but before I ran that gedit command, I was getting native resolution my LCD at 1280x800 ore something like that.

---

### Post by overdrank on 2008-08-01
> **Wild Squid said:**
> Well, don't have a video card, but before I ran that gedit command, I was getting native resolution my LCD at 1280x800 ore something like that.

Ok use the command ```
lspci 
``` in the terminal located under applications, accessories and then look for VGA in the output. This will be your graphics and then maybe we can help more. 
Also have you looked under system, administration, hardware drivers to see if any drivers are listed?

---

### Post by Wild Squid on 2008-08-04
I'm not quite sure what I did, but the native resolution options did come back.

---

