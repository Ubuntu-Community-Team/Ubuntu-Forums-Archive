---
title: "Webcam on video1"
date: 2009-06-11
forum: Hardware
---

### Post by nengracia on 2009-06-11
I have a TV capture card installed using video0. When I plug in my webcam, it creates video1 but doesn't work - perhaps it also uses video0.

How do I "instruct" my webcam to use video1 instead? I can have TVTime use video1 within the tvtime.xml file so that video0 can be used by the webcam. Unfortunately, the webcam still doesn't work.

I want to doodle around to figure out things. Can anyone show me how I could have my webcam use video1?

---

### Post by Ferrat on 2009-06-11
What program are you using to watch your webcam?

Not using like amsn or something that might lock the cam for it's own use?

---

### Post by nengracia on 2009-06-11
nope, I'm not using any of those. I tried using cheese but no image is coming out of the webcam.

i wanted to use ekiga or skype for the webcam.

---

### Post by Ferrat on 2009-06-11
Can you select/see the /dev/video1 in edit>>preference? 

what do you get when doing 
```
lsusb

```
??

---

