---
title: "Google earth 5"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by cl333r on 2009-02-03
Hi folks,
is it just me or is the newly released google earth 5 beta for Linux not supporting the "underwater" feature?

---

### Post by ferrarix on 2009-02-05
Does anyone have the same problem I got? It closes as soon as I load it.

This is what I get in the terminal:
> franco@ubuntu:~$ googleearth
Warning: Unable to create prefs directory '/home/franco/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
franco@ubuntu:~$ 

Edit: BTW, I am on Ubuntu 8.10 Inteprid Ibex, AMD64, IntelCore2Duo.

---

### Post by ferrarix on 2009-02-05
Okay fixed it.

Found the fix on [this]("http://blog.mymediasystem.net/avchd/google-earth-5-crashes-on-linux/") link.

Quote:

> Google Earth 5 for Linux crashes. You can solve this problem by renaming libcrypto.so.0.9.8 to something else. But be careful, there are probably more than one file with this name on your hard disk drive.
Be sure, the file you rename resides in the googleearth folder.
Do the following:

[QUOTE]find / -xdev -name "libcrypto.so*" | grep google

change into the directory you found above, and rename the libcrypto.so.0.9.8 file into
something else:

> cd <googleearth directory>
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.nouse[/QUOTE]

---

### Post by ferrarix on 2009-02-05
Now I got another problem. The images are all flickering. I'll try playing with my ATI driver (which is updated already through EnvyNG) and OpenGL.

---

### Post by TAFKARS on 2009-02-05
> **ferrarix said:**
> Now I got another problem. The images are all flickering. I'll try playing with my ATI driver (which is updated already through EnvyNG) and OpenGL.

Same flickering trouble for me, but the fix to load googleearth worked just fine.  Anyone else able to overcome this? Screen looks as per the attachment.

---

### Post by Saiph on 2009-02-05
I installed googleearth 5, LOL:
Another crash happened while handling crash!

---

### Post by ferrarix on 2009-02-05
Something tells me that this is more of a Google Earth 5 problem rather than an Ubuntu thing. I'll be happier if Google issues an update fix/patch/release to it rather than us trying to figure out a workaround.

Still, if anyone has any solutions, it would be greatly appreciated :).

---

### Post by TAFKARS on 2009-02-05
> **ferrarix said:**
> Something tells me that this is more of a Google Earth 5 problem rather than an Ubuntu thing. I'll be happier if Google issues an update fix/patch/release to it rather than us trying to figure out a workaround.

Still, if anyone has any solutions, it would be greatly appreciated :).

Yeah, maybe. It seems that plenty of other users are trouble free, though.

[http://ubuntuforums.org/showthread.php?t=1059564&highlight=google+earth](http://ubuntuforums.org/showthread.php?t=1059564&highlight=google+earth)

---

### Post by ferrarix on 2009-02-05
Thanks. I just asked whether someone is using it in a similar environment to that of mine. Let's see.

---

### Post by InvaderZim73 on 2009-03-15
Hi folks,

I have exactly the same behaviour.
Installed Google Earth 5.0 and have a flickering view to it.
After some time I found some hints how to fix that nasty libcrypto thingy.
I am using a ATI HD4850 graphics card with the 9.2 catalyst.

Till now I have no cure to the flickering stuff.

Any news from your side?

Greetz InvaderZim73

:popcorn:

---

