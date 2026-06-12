---
title: "Diagnosing Hardware/software Issue"
date: 2010-10-31
forum: Hardware
---

### Post by shanksy75 on 2010-10-31
Hi all,

I have a problem getting the webcam working on my Acer Aspire One.

It says it can't detect the device video0.
I have tried re-installing both UNR and the original Linpus Lite without success.
As these webcams are known to fail I replaced the hardware but still get the same error message when starting cheese.

I'm not really sure where to try from here.  If there is a motherboard issue I wouldn't have a clue how to diagnose this.

Any help is greatfully received
Lee

---

### Post by IcarusR on 2010-10-31
Is it enabled in the bios, or are there any Fn combinations that toggle it on/off ?

---

### Post by shanksy75 on 2010-10-31
Ive just tried all the function keys and none of them toggle the webcam.

There is no option in the BIOS to enable / disable ?

---

### Post by IcarusR on 2010-10-31
To identify make of webcam from a terminal run this command & post output (will list all usb items with ids)

```
lsusb
```

You can then search forum for your webcam id & see if there are any helpful posts.

---

### Post by shanksy75 on 2010-10-31
Terminal output for lsusb is :

Bus 005 Device 001:  ID 0000:0000
Bus 004 Device 001:  ID 0000:0000
Bus 003 Device 001:  ID 0000:0000
Bus 002 Device 001:  ID 0000:0000
Bus 001 Device 001:  ID 0000:0000

---

### Post by shanksy75 on 2010-10-31
Have also ran the video test in gstreamer-properties for both vfl and vfl2 :

Error running pipeline 'Video for linux (v4l)' : Could not open device "/dev/video0" for reading and writing.  [v4l_calls.c(179): gst_v4l_open () : /pipeline0/v4lsrc3:
system error: No such device or address]
-----------------------------------------------------------------------------
Error running pipeline 'Video for linux 2 (v4l2)' : Could not open device "/dev/video0" for reading and writing.  [v4l2_calls.c(418): gst_v4l2_open () : /pipeline0/v4l2src2:
system error: No such device or address]

---

