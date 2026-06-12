---
title: "intel 945 GM video with TA spring"
date: 2009-04-14
forum: Hardware
---

### Post by polymath on 2009-04-14
Anyway, i'm running an acer aspire 3680 laptop with the 945 GM video card.  Support for intel cards is *supposed* to be included with default ubuntu.  I'm running a multi-DE intrepid (and i have all the standard ubuntu tools installed).  I installed TA spring and for some reason the map appears all gray.  Spring's help page says that this is due to "some unimplemented openGL function".  This leads me to believe that the video driver i have is inadequate.  I tried to install the drivers from intel but it didn't work even though i have the linux-headers-* package installed.  Can someone help me get the graphics card working.

---

### Post by WhiteHorse on 2009-10-02
This worked for me:
Try installing driconf with apt and enabling S3TC Texture Compression under the image quality tab.

After installing driconf, go to System->Preferences->3D Acceleration->Image Quality->Enable S3tc

Cheers!->Ubuttu 9.10 Alpha 6

---

