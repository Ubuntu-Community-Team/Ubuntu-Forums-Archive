---
title: "phillips spc230nc webcam"
date: 2008-12-12
forum: Hardware
---

### Post by becominglumberg on 2008-12-12
I have been looking around, and all I can find is the pwc 'driver', which is unmaintained since 2006. Anyone know how to get this webcam working?

-Guy

---

### Post by tagno25 on 2008-12-12
I also just got a Philips SPC230NC.  I cannot even get the old drivers to compile in Intrepid Ibex(8.10).

---

### Post by fireman300 on 2009-01-20
Got it to work tonight. I've been trying for a couple weeks now. The quality is not that good and the frame rate is very slow. But it works. I installed the latest GSPCA (gspca-e2d12cf2df01). 

Mainly I used this reference: [http://kubuntuforums.net/forums/index.php?topic=3100501.0](http://kubuntuforums.net/forums/index.php?topic=3100501.0)

But I've also consulted the following: 
[http://kubuntuforums.net/forums/index.php?topic=3098024.0](http://kubuntuforums.net/forums/index.php?topic=3098024.0)
[http://kubuntuforums.net/forums/index.php?topic=3099982.0](http://kubuntuforums.net/forums/index.php?topic=3099982.0)
[http://kubuntuforums.net/forums/index.php?topic=3096810.0](http://kubuntuforums.net/forums/index.php?topic=3096810.0)

Basically just follow the instructions, download the latest and greatest, untar into /tmp, cd into /tmp/gspca*, run "sudo make all" (no quotes), run "sudo make install" (no quotes). The details are in the references. It took me a few tries to get it to compile correctly and work but now it does. 

Hope this works for others too.

---

### Post by cristianrosa on 2009-07-12
I bought this camera in november 2008, and it didn't worked, so I searched a bit and realized it uses a pac7311 sensor (made by pixart), but the vendor ID wasn't associated to it.
I sent an email to the guys maintaining the v4l repos with the ID they added it to the module, that is why now it works with the last version of gspca (which didn't make to the kernel yet).
The low framerate (and over exposed red image) is produced because the auto exposure algorithm implemented in the gscpa module defines some ideal "knee values" for exposure time, and it iterates trying to converge to them. In each iteration it adjust the exposure and then read the luminance (and some other values) and recalculate the increments for the next step. The problem is that the knee values choosen are too high for this camera (i don't know why) and when it tries to converge, the exposure time goes up to 8 seconds or more! so the framerate drops, and the image get overexposed. What I did was to modify this default knee values, and now it works a lot better, with higher rates and good colors, but it is not perfect, the hack is quite primitive :)
I sent a second email with this explanation, but I got no answer.

---

### Post by borisz264 on 2009-08-03
Could you please post some details on how you adjusted the "knee value"??

I have finally gotten the driver working, and have the red overexposed, low frame rate problem you described.

If you have an even better solution by now, that would be awesome as well!

As it is, this is unusable.

Also, does your webcam also only work in Cheese?

For me, skype and other programs just show a green/pink screen(though the static over it changes slightly if i put my thumb over the lens)

---

### Post by cristianrosa on 2009-09-24
Hi! sorry for the delay, I forgot to subscribe to the bug report :S

About the modifications I attach a patch that you can apply to the sources.

For using the webcam with skype, you need to launch it like this:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

And oviously, you need to install v4l1 compatibility library.

This is necessary because the new gscpa driver was ported to v4l2 and skype expects a v4l1 driver, so this library makes the convertion. You can download it from the mercurial repository of v4l. (maybe it is in the ubuntu repo, but I don't know)

If you find any information about how to improve this, please tell me, because each time the kernel is updated, I have to manually rebuild the modules, and it sucks.

---

### Post by sladetf on 2010-05-26
critianrosa:

did you rebuild gspca from source? i am trying this in lucid lynx and can'd find gspca.c or pac7311.c to run the patch against....

cheese works, but i'm getting the same overexposed, slow, saturated images as described above...

i'm not very terribly good yet with ubuntu modules/driver customization.. thanks for any insight anyone can provide

-t

---

