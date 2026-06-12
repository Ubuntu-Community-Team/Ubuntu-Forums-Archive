---
title: "gphoto2 2.4.2 build not working."
date: 2008-09-23
forum: General Help
---

### Post by RimBlock on 2008-09-23
Hi, 

I am using the latest version of UBuntu

There is a bug in gphoto2 2.4.0 (latest in Synaptic) which makes it useless for my camera (Canon 5D).

I have uninstalled 2.4.0 (which caused f-spot, gthumbs etc also to be uninstalled) and installed all dependencies listed in the gphoto2 2.4.2 tarball README.  I also installed the build-tools from Synaptic and a few other items reported missing at configure / build time.

After running the configure, make all and make install the versions seem to check out and no errors were reported.
Gphoto2 2.4.2
libgphoto2 2.4.2
gphoto-port 0.8.0

make check also reports no errors.

Running gphoto in capture-preview mode take a snap and then reports premeture end of jpg.  The file produced cannot be opened by pic preview or anything else.

Running gphoto in capture-image mode takes a snap but then hangs and comes back with a generic error message (the photo is on the camera).

Running in debug mode produces a log file that looks reasonible although large as it tries all cameras it has configs for multiple times but it tries to read 64 bytes (from memory) and fails near the end of the log and fails 1000 times.  It seems to get the exif info back and I am wondering if this is what it is saving in the file as the log reports the only significant amount of data read as containing the camera make and model etc.

The camera is currently in PC mode and on automatic settings for speed / f-stop / ISO etc.  The camera auto off has been turned off. 

Any ideas / information required which may help to sort this out.

I am trying to use it for the timelapse function.

Many thanks
RB

---

### Post by RimBlock on 2008-09-23
Anyone,

gphoto2 only has a mailing list and no support forum I can find.

Only two options I can see at the moment is to write a script that calls the image capture function and then after a couple of seconds kills gphoto2 (after it has taken the snap) then pauses and repeats the process.  Not ideal.

Other option is to go and buy the timer remote which is pretty expensive but which works out of the box.

Cheers
RB

---

