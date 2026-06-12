---
title: "Best Budget Webcam: QuickCam Messenger (MS VX-1000 and QC Connect don't work)"
date: 2008-08-28
forum: Hardware
---

### Post by wizard8080 on 2008-08-28
So after three of the more inexpensive webcams, finally, the Logitech QuickCam Messenger works out of the box on Ubuntu 8.04 Hardy.  ASIN: B00111HSJ8 Item model number: 960-000161.  Both the cam and microphone work in Skype.

Tried both the QuickCam Connect and the MS LifeCam VX-1000; neither work properly as of 8/2008.  Suspect the drivers will be updated eventually.  Also suspect the VX-3000, which is a great deal on Amazon doesn't work either, but haven't tested.

---

### Post by jesterthejedi on 2008-12-24
Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file
extract and change directory
in terminal type "make" no quotes take about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

---

### Post by rbolio on 2009-02-23
I guess ill be trying jesterthejedi's method! i'll be buying mine today!.

---

### Post by rbolio on 2009-03-02
make it a tutorial! it worked to perfection in the first go! :D thNks!

---

