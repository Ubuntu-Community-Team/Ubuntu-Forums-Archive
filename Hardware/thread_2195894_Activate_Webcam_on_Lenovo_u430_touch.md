---
title: "Activate Webcam on Lenovo u430 touch"
date: 2013-12-27
forum: Hardware
---

### Post by moengac on 2013-12-27
Sorry if i sound like a beginner but I installed the latest version of Ubuntu (13.10) and have had a hard time activating my built-in webcam. I'm able to use an external webcam and its recognized by the Cheese Webcam Booth app. Cheese does have the option to select the in built webcam (Lenovo EasyCamera--dev/video0) but the webcam viewer is pitch black. Please someone help..

---

### Post by mörgæs on 2013-12-27
Please run **lsusb** and post the results in CODE tags.

---

### Post by moengac on 2013-12-27
```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 13d3:5173 IMC Networks 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 04f3:0153 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by mörgæs on 2013-12-28
Sorry, I don't know the 
```

Bus 002 Device 004: ID 13d3:5173 IMC Networks 

```
webcam. 

Have you tried installing Guvcview?

---

### Post by moengac on 2013-12-30
Yes I have, in the app it works with a slight flicker. . I've figured out how to manually get it to work by going to global settings and giving the websites I needed special permission by never asking. However I get a flicking green screen and can see a little of the webcam working.

---

