---
title: "cant get native screen resolution on acer travelmate 4000"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by ludicrouSpeed on 2007-01-07
Hi all,

I have attempted to install ubuntu 6.10 on an acer travelmate 4000. the installation runs fine, but the problem is when i start it up it runs in 1024x768! the laptop is a widescreen, but my only choice of resolutions is 1024x768,800x600 or 640x320.

the weird thing is when i checkout the xorg.conf file, it says the resolution only which is 1280x800 which is the native resolution i want. there is no mention of 1024x768 in the xorg.conf so i think its pretty weird.

i had the same problem when i installed 6.06 but got around it with the help of a friend, the problem is i dont remember what he did.

i have tried doing this

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)


but it did not fix it.


Any ideas?


Thanks in advance

Ludi

---

### Post by Travisty on 2007-01-07
I think the problem resides with your integrated Intel graphics card. I have the 915 chipset and it automatically allocates memory from my system memory as needed. The problem is when the system boots it only starts with enough memory to push 1024x768.

The work around is to install a application called 915resolution. I don't know if you need to enable the extra repositories for this or not. just run the following:

sudo aptitude install 915resolution

that should trick the OS in to think the video card has more ram, thus allowing you to run a higher screen resolution.

---

### Post by ludicrouSpeed on 2007-01-08
thanks a lot, i did what you said and it worked great!

however, when i do things like dragging a window around, scrolling through an email or browser, the screen redraws seem slow and garbled, reminds me of when you dont have the correct graphics driver installed in windows, do you have any tips for this?

Thanks a lot,

Ludi

---

### Post by jacod on 2007-01-10
Hi,

I have exactly the same issue with a TM4020, which also has a i915GM card. Installing the 915resolution tool solved the problem with the screen resolution, but the wm is slow when dragging windows or maximizing/minimizing.

The card seems to be correctly recognized and the i810 driver is loaded with glx support, as glxinfo shows:

```

#~ glxinfo | grep direct
direct rendering: Yes
#~ 
#~ glxinfo | grep renderer
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225

```

glxgears runs over 1000 fps. However, GL screensavers are slow, as if running on software acceleration. Other apps run smoothly, and there is not an intensive use of cpu.

Thanks in advance,
David

---

### Post by ludicrouSpeed on 2007-01-10
Yes, i have noticed that the screensavers are incredibly slow, the funny thing is, when i had 6.06 installed, the screensavers ran much more smoothly.

Are we just being fussy?

Naaaah, we want to be able to showoff ubuntu!

Anyone have any ideas?

inTHANKSadvance

Ludi

---

### Post by pavan_bitsgoa on 2007-06-12
thank u one and all

this works really fine and no need to install any new driver

---

