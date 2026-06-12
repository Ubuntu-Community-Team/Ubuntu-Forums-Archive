---
title: "Dell Inspiron Webcam only works with some apps"
date: 2011-11-06
forum: Hardware
---

### Post by tradecraft1 on 2011-11-06
I cant figure this one out. I have a Dell Inspiron 1521 with Ubuntu 11.10 that has a OV2640 Webcam. It works fine with Skype and VLC but not with amsn or Cheese. I see no errors when launching amsn or Cheese from Terminal. 

Amsn says no webcam found during setup and Cheese just shows a blank grey window. The blue webcam indicator light does come on when Cheese starts.

Any thoughts?

---

### Post by pfnorris on 2011-12-22
As far as I have been able to discover there appears to be some issue between v3.0 kernel and UVC video module. Reloading the module works on my Dell Inspiron which uses this device. You might find [this link]("http://ubuntuguide.net/fix-dell-1420-webcam-not-working-in-ubuntu-10-04-lts") useful. It worked for me in 11.10

---

