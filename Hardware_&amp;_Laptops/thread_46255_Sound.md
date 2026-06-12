---
title: "Sound"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by SpEcIeS on 2005-07-03
When using Gnome the sounds works well aside from some apps such as realplayer (which does not work at all), some OpenGL games such as gl-117, and others. Now, I understand that realplayer must have esd stopped in order for it to work, so is this the same problem with the other apps and what would be the workaround? Currently I use fluxbox, which was compiled and installed manually, to use the other apps, but the gnome applicatioins, such as gnome games, do not have sound.

How does one configure the to to cross and work properly?  :? 

Thanks for any help in this matter. :)

---

### Post by Karlos on 2005-07-04
getting the sound to work properly needs a bit of tweaking, it requires something called software mixing

look at the following threads

[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound)

I found the above info very handy

regards

Karlos

---

### Post by SpEcIeS on 2005-07-04
Thanks for the help. I will be sure to read these. :)

Update:

I read the two threads, and had success with running multiple sounds in fluxbox, including gnome apps, however, while in gnome, the sound seems to be the same. Games such as gl-117 do not have sound. In gnome AudaCity does not seem to see the device, which works in fluxbox.

Any ideas?  :???:

---

### Post by Karlos on 2005-07-05
try setting audacity too use alsa for output rather than oss 
(somewhere in the preferences)

---

### Post by SpEcIeS on 2005-07-05
[QUOTE=Karlos]try setting audacity too use alsa for output rather than oss 
(somewhere in the preferences)[/QUOTE]
Yeah..  I asumed that, but could not find it. Upon this post I looked again, and also found nothing. The only thing I could find regarding I/O is Device: /dev/dsp for Recording and playback. I do not really know what to do from he except when using certain sound apps to logout of Gnome and use fluxbox. :)

---

### Post by Karlos on 2005-07-06
I just remembered the audacity in universe doesn't have alsa/jack support

dont panic tho there is a solution

[https://wiki.ubuntu.com//MOTUAudio](https://wiki.ubuntu.com//MOTUAudio)

have a look at the above link if you add their repository to your /etc/apt/sources.list you will be able to get a version that has alsa/jack support from there

well worth a look anyway if your into audio software

---

### Post by SpEcIeS on 2005-07-06
Thanks for the help  :) , however it would not let me upgrade my audacity due to libvorbis version issues. It would seem none of my listed repositories contain the necessary packages to allow upgrading. This is also true for my gstreamer 0.8 lame package. In order for it to be upgraded I need libc6 (>=2.3.2.ds1-21), but I have 2.3.2.ds1-20ubuntu13 installed. Currently I do not know where to attain these packages.

Any ideas?  :neutral:

Update:

Found the libc6 packages, but from what I am reading, in some areas, it may not be wise to do this. Is this true, or should I go ahead and install the required packages?

---

### Post by Karlos on 2005-07-06
if I remember rightly I think I got the libvorb stuff from the demudi repo and everything seems to be fine

add this to your sources list

deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) testing main

let me know if it works

---

### Post by SpEcIeS on 2005-07-06
Well **Karlos** that fixed the problem and I upgraded the libc6. :) Thanks for the help. :)

There sure are a lot of upgrades there, however some of the installs remove other apps, and devs, that I use. Not only did that repo fix the audacity and libc6 issues, but some other apps were updated also. A well rounded encounter.  ;-)

---

### Post by Karlos on 2005-07-11
No problem

---

