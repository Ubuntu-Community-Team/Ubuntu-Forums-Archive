---
title: "Logitech cam and Cheese"
date: 2009-05-18
forum: Hardware
---

### Post by OMRebel on 2009-05-18
I have a Logitech Quickcam Pro 4000 that freezes whenever I try to record video in Cheese.  I've searched, and I see that it's a common problem with Logitech cams, but I can't find a solution.  Here's some additional information:

Result from lsusb for the cam:
*Bus 005 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000*

When running Cheese from the console, and I click to start recording, I get a black screen for a second or two, then a still image.  If I click on Stop Recording, then the screen goes black and the window grays out.   The only thing I see in the console is:

*GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps*

I have to then force the application to stop at that point.

I'm running 9.04 by the way.

Anyone have any ideas?

---

### Post by Dark_Stang on 2009-05-18
I have an old (as in OLD) logitech cam that worked fine in camstream but hated anything else. Have you tried that yet?

Note: I haven't used camstream in years.

---

