---
title: "linux(guest) receiving garbled USB from windows(host)"
date: 2009-12-21
forum: Hardware
---

### Post by JasonSpradlin82 on 2009-12-21
i have a webcam supported by uvcvideo, and it can be found, but the data that comes through from the windows host, through virtualbox usb, into linux seems to be mildly corrupt, as the video is very, very garbled.  (see screenshots)  gstreamer-properties, when run from the terminal, reports back a lot of what seem like anomalies in the video stream, and upon much research, the most I have found is that, at some point, somebody submitted a patch for uvcvideo for VMWare installations passing USB video to the linux guest.  I don't really know enough to know what to do with this patch, if it is even still viable for the latest UVC version.  I can't seem to get it to work and don't know where to go from here.

The patch itself is almost two years old, and although I've submitted a support request on the uvcvideo site, it seems that no support requests have been looked at in about as long (two years or so).  

here is the patch page:

[http://developer.berlios.de/patch/?func=detailpatch&patch_id=2323&group_id=5681](http://developer.berlios.de/patch/?func=detailpatch&patch_id=2323&group_id=5681)

What can I do to get this working?  I've installed the latest version of UVCvideo, but that did not seem to help.

---

