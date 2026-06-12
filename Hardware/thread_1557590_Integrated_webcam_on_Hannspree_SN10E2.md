---
title: "Integrated webcam on Hannspree SN10E2"
date: 2010-08-21
forum: Hardware
---

### Post by riprydah on 2010-08-21
I just installed Ubuntu Netbook 10.04 on my Hannspree netbook. I tried using the integrated webcam via Cheese but I get an error message that says "No Device Found".

I'm a first time Ubuntu (or Linux) user, so any help would be appreciated. Thanks.

---

### Post by lukeiamyourfather on 2010-08-21
If the camera is Video4Linux 2 capable then it should show up in /dev as video0, video1, etc. If you don't see any video items in /dev then the camera might not work with Linux. In a terminal run this to see what's in /dev.

```
ls /dev | grep video
```

---

### Post by riprydah on 2010-08-21
[FONT=Arial]I entered that code and had no result. Guess it's not compatible w/ Linux then?[/FONT]

Any other suggestions or should I call it quits in trying to resolve this issue? Thanks!

---

### Post by lukeiamyourfather on 2010-08-22
> **riprydah said:**
> [FONT=Arial]I entered that code and had no result. Guess it's not compatible w/ Linux then?[/FONT]

Any other suggestions or should I call it quits in trying to resolve this issue? Thanks!

As far as I know that's the end of the road for it. Either look for a camera that uses that API or just don't use a camera. 

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

Note there are some cameras that will work that are not on that list, but the list is a good starting place.

---

### Post by Lucky2BeHere on 2011-11-18
I'd like to know if there are any updates on camera and mic support for the Hannspree SN10E2. I'm running 11.04 Natty and neither works. Just trying to get Skype in order!

---

### Post by Lucky2BeHere on 2011-11-18
Am upgrading to 11.10 today. Will see if that helps. The notes claim plug-and-play with cameras...

---

