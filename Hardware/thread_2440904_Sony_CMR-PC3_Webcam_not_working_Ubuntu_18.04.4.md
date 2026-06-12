---
title: "Sony CMR-PC3 Webcam not working Ubuntu 18.04.4"
date: 2020-04-16
forum: Hardware
---

### Post by ibod on 2020-04-16
Hi,

I have a Sony CMR-PC3 Webcam  
Bus 001 Device 003: ID 054c:0067 
Ubuntu 18.04.4 LTS
Dell Optiplex 3010

it's there in lsusb 

But Cheese reports "No device found"

Ive tried googling and searching the forum, but no luck

Can anyone help

Thanks

---

### Post by mörgæs on 2020-04-16
Does Guvcview connect to the camera?

---

### Post by ibod on 2020-04-16
Hi, 

No Guvcview does not connect to the camera 

It reports error "No video device found"

---

### Post by mörgæs on 2020-04-17
Googling a little deeper seems to indicate that no driver is available, or at least wasn't in May 2017
[https://www.raspberrypi.org/forums/viewtopic.php?t=184873](https://www.raspberrypi.org/forums/viewtopic.php?t=184873)

You could try a live boot of 20.04 to see if anything has changed but I am afraid chances are slim.

The Debian list is not the absolute truth. I have a working webcam which is not stated there.

---

