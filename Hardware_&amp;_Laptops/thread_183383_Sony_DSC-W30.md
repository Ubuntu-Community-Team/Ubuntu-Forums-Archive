---
title: "Sony DSC-W30"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by Evan_G on 2006-05-27
Hi there.  I don't have much hope that I can be helped with this right now, but I figured I would ask in case someone has any ideas.

I just purchased a Sony DSC-W30 camera.  The device has been detected, but when I try to import the files I get this error:

```

An error occurred in the io-library ('Could not claim the USB device'): 
Could not claim interface 0 (Operation not permitted). Make sure no other 
program or kernel module (such as sdc2xx, stv680, spca50x) is using the device
 and you have read/write access to the device.

```


Could this be a driver issue?  I do not see this camera model listed on the hardware compatibility lists.

---

### Post by adamkane on 2006-05-27
Maybe the camera is trying to access a folder that doesn't exist or that doesn't have write access enabled?

---

### Post by azurelight1337 on 2007-08-25
Odd, mine works fine without any configuration.

---

### Post by elfontain on 2007-08-26
I have the Sony Cyber-shot DSC-W55 and I too recieved the same message. Hopefully there is a "patch" or driver we can download...?

---

### Post by elfontain on 2007-08-26
Just figured it out.  By going to the "Setup 2" page in the camera and changing the "USB Connect" to PTP,  I was able to solve the problem.

---

### Post by tlsarles on 2007-08-31
Thank you elfontain, that is exactly what i needed. Too bad I didn't find this post before I tried all the other junk!

---

