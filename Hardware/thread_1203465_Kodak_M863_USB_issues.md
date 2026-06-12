---
title: "Kodak M863 USB issues"
date: 2009-07-03
forum: Hardware
---

### Post by lile001 on 2009-07-03
I get error messages when I try to connect a Kodak M863 digital camera via USB. 

Usually I will get an error message stating "Unable to mount: Error in itializing camera -60: Could not lock the device".  Some other errors have occurred occasionally occurred.  

If I try to mount the camera, that generates the same error.  

After all that, sometimes the file browser eventually opens the camera drive.  Sometimes not. Also, F-Spot Photo Manager is sometimes able to read pictures.  Sometimes not.  

Personnally, I'd rather skip the goofy photo manager and just copy the photos to my hard drive then erase them off the camera.  If I want to "manage' them I can do that later.  But that requires mounting the device! 

Once the file browser or F-Spot finally decides it can talk to the camera, everything works OK.  That happens maybe 25% of the times I plug the camera in.

---

### Post by lile001 on 2009-07-04
> **lile001 said:**
> I get error messages when I try to connect a Kodak M863 digital camera via USB. 

Usually I will get an error message stating "Unable to mount: Error in itializing camera -60: Could not lock the device".  Some other errors have occurred occasionally occurred.  


OK, well i learned one thing by messing around with it.  the "SHARE" button on the back of the camera accomplishes better communication with Ubuntu.  Although USB communication is flaky normally, if I turn on the camera first, plug it into the computer second, and then press the "share" button on the camera, Ubuntu can read it every time.  I think this sequence may be important.  If I plug the camera in first, then turn it on, I'm not sure it works the same.  

The "Share" button, in Windows systems, alerts the goofy Kodak Photo manager program that the camera is ready for it, I had no idea it also alerts Ubuntu that it is ready to talk pretty as a storage device.  

Hope this helps someone else!

---

### Post by StepNjump on 2012-02-20
Lile001, thank you very much. That works great for me too.

Thanks for your post.

StepNjump


> **lile001 said:**
> OK, well i learned one thing by messing around with it.  the "SHARE" button on the back of the camera accomplishes better communication with Ubuntu.  Although USB communication is flaky normally, if I turn on the camera first, plug it into the computer second, and then press the "share" button on the camera, Ubuntu can read it every time.  I think this sequence may be important.  If I plug the camera in first, then turn it on, I'm not sure it works the same.  

The "Share" button, in Windows systems, alerts the goofy Kodak Photo manager program that the camera is ready for it, I had no idea it also alerts Ubuntu that it is ready to talk pretty as a storage device.  

Hope this helps someone else!

---

