---
title: "Laptop Webcam Compatability"
date: 2008-08-29
forum: Hardware
---

### Post by stat30fbliss on 2008-08-29
I could be jumping into this post, because I dont quite have much info on the subject, so I will keep it vague for now, and return with more info at a later date.

My webcam doesnt work with Ubuntu.  It is build into my laptop.  I did not buy name brand.  I bought it through CyberPower, and the name of My Cam is unknown.  My laptop shipped with BisonCam preloaded, which I effectively lost, and now I am not sure what model it is.  

The cam works, and is autodetected in windows, how can I find out if it is compatible with Ubuntu?  It wont even make a little noise when I hit the on off button.  Is it a dead cause?

Thanks

---

### Post by IntuitiveNipple on 2008-08-30
When running Linux, use these commands to report details of the device:
```

lsusb

udevinfo --query=all --name=/dev/video0 --attribute-walk

```

---

