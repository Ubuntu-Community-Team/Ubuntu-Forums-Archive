---
title: "Webcam (via Cheese) stopped working in 8.10"
date: 2008-12-21
forum: Hardware
---

### Post by corwinspyre on 2008-12-21
Hi!

I have an HP tx 2500 laptop with a webcam.  It worked fine without configuration on 8.04, and I recorded videos and pictures with the program cheese.  Since then, I did a full reinstall of 8.10 (upgrading broke lots of things), but now it won't work.  I start cheese, and a blue light near the camera comes on, so I assume it can find it.  However, it won't show a picture on the cheese main screen, and when I try to take a picture or record a video, it immediately crashes out.  I started it from terminal to catch the errors.  The first quote is it starting, and the second is what is outputted when I try to record.  You can see it segfaults out.

> 
  $ cheese
/home/zxcv/.themes/UbuntuStudio/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/home/zxcv/.themes/UbuntuStudio/gtk-2.0/gtkrc:213: Unable to locate image file in pixmap_path: "panel.png"
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:13054): WARNING **: could not generate thumbnail for /home/zxcv/Webcam/0006.ogv (video/ogg)


(cheese:13054): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:13054): WARNING **: could not generate thumbnail for /home/zxcv/Webcam/2008-12-18-105020.ogv (video/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:13054): WARNING **: could not generate thumbnail for /home/zxcv/Webcam/2008-12-20-165329.ogv (video/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:13054): WARNING **: could not generate thumbnail for /home/zxcv/Webcam/0004.ogv (video/ogg)


(cheese:13054): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:13054): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

This is after I hit record video:

> 
(cheese:13054): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small


(cheese:13054): GStreamer-CRITICAL **: gst_caps_get_structure: assertion `GST_IS_CAPS (caps)' failed
Segmentation fault


Thank you very much for your help!  Please let me know if there's any other info needed.  In cheese's preferences, the camera is "CKF7073 (/dev/video0)".  Changing the resolution doesn't help, though the default should work anyway (640x480).

---

### Post by jsully1 on 2008-12-22
Having this same exact problem on my Mini 1000 - the light comes on but nothing shows up.  Launching from terminal yields the same error message.

---

### Post by BilliShere on 2008-12-28
Its easy to fix this problem guys! I got the solution from this page: link removed

here is the file they linked: link removed

extract it
open a terminal in the new extracted folder
type in make
then type in sudo make install
then restart your laptop and fire up cheese! it should work flawlessly.
if not you probably need drivers..
get easycam to download and install drivers for your webcam.


EDIT: Its not working anymore....I may have to try to get the newer versions of cheese or libv4l from jaunty jackalope or summin

---

### Post by hard2explain on 2009-01-02
I think I'm having the same problem here so I'd like this solution sorted too if it's possible.

---

### Post by the12plus on 2009-01-03
I used to have quite the same problem with Ubuntu 8.10 on an Acer Aspire One 150L, but now, having realized that it all has to do with libv4l-0, I got myself a workaround by downgrading libv4l-0 from 0.5.6-1 to 0.5.0-3.

To downgrade libv4l-0 from 0.5.6-1 to 0.5.0-3, do the following:

-Open Synaptic Package Manager
-Select libv4l-0
-Go to Package->Force Version and choose 0.5.0-3~interpid1
-Apply changes

Hopefully, Cheese now works fine.

If this new set-up is successful for Cheese and you don't want libv4l-0 to be constantly in the updates list, you can lock this version, although this is generally not recommended, essentially for the same reasons that downgrading is discouraged. If you decide to lock this version, select libv4l-0 (in Synaptic) and go to Package->Lock Version.

Hope this works for you as well, since such problems are often a bit irritating...

---

### Post by bjornd on 2009-01-04
Confirmed working on a HP tx2020.

---

### Post by stmiller on 2009-01-04
I had the same problem. I did not downgrade the package, but rather had to pick a low camera resolution in the cheese prefs (160x120), then it works. Hope this helps,

---

### Post by the12plus on 2009-01-04
Lower resolutions would also work for me, yet neither 640x480 (max) nor 320x240 would work until I downgraded... As a matter of fact I had been mostly disappointed being obligated to use 160x120 or something similar as maximum resolution...

---

