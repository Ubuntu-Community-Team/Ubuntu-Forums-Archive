---
title: "Terminals with Nvidia"
date: 2008-08-29
forum: General Help
---

### Post by gali98 on 2008-08-29
Okay I don't really know the correct term for this, but you know when you press ctr+alt+F* and you have terminals F1-6 or so and you usually have X running on F7 and whatnot.

Anyway with the Nvidia graphics, those terminals don't show up.
I think this is known, however does anyone know how to get those to work?
Well, technically they work, but you can't see anything so you have to type by heart :)

Some info on my system:

HP Pavillion TX2000z

Nvidia Geforce 6150 Go

nvidia-glx-new


If anyone could/would help I would appreciate!

Kory

---

### Post by Fixman on 2008-08-29
> **gali98 said:**
> Okay I don't really know the correct term for this, but you know when you press ctr+alt+F* and you have terminals F1-6 or so and you usually have X running on F7 and whatnot.

Anyway with the Nvidia graphics, those terminals don't show up.
I think this is known, however does anyone know how to get those to work?
Well, technically they work, but you can't see anything so you have to type by heart :)

Some info on my system:

HP Pavillion TX2000z

Nvidia Geforce 6150 Go

nvidia-glx-new


If anyone could/would help I would appreciate!

Kory

Are you sure they don't work? I also use nVidia video cards and my ttys work perfectly.

---

### Post by gali98 on 2008-08-29
Well as I said, they work, but I can't see anything (i.e. a black screen).
With the restricted driver turned off they work fine, but I dont have the restricted driver..... Which I need.
So Yes I am sure.. :)

Kory

P.S. Thanks for replying though.

---

### Post by gali98 on 2008-08-31
Bump....

Is anyone else at least having this problem?
Kory

---

### Post by Sycron on 2008-08-31
> **gali98 said:**
> Well as I said, they work, but I can't see anything (i.e. a black screen).
With the restricted driver turned off they work fine, but I dont have the restricted driver..... Which I need.
So Yes I am sure.. :)

Kory

P.S. Thanks for replying though.

I don't understand, you mean you can't install restricted drivers ?

---

### Post by hoarycripple on 2008-08-31
I had this problem at some point.  Google "ubuntu blank tty" and you get lots of hits.  I'm not sure if you are having an intiramfs problem or if it is truly a nvidia driver problem.  Some of those hits you get might help you sort out where the problem is.

---

### Post by jerome1232 on 2008-08-31
I don't know if this is the cause or not but it could be they are just in a resolution your monitor doesn't support?

Try manually changing it to another resolution with this guide
[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)

---

### Post by gali98 on 2008-08-31
Thanks guys, I will check it out!
Kory

---

### Post by gali98 on 2008-09-13
Well neither really worked.

The problem is with framebuffers and the like.

the ubuntu tty blank search gave what I needed, but it didn't work right.
You have to whitelist framebuffer stuff. Basically since I have the closed nvidia driver it doesn't work well (and in my case at all) so I'm not going to worry to much about it.

right now there is a bug for at launchpad that has a LOT of attention so maybe it will get fixed sooner or later.

Thanks guys...

Kory

---

### Post by fsmithred on 2008-09-13
I had the same problem in gutsy and was able to fix it and use the proprietary nvidia driver. 

[http://ubuntuforums.org/showthread.php?t=577457](http://ubuntuforums.org/showthread.php?t=577457)

---

