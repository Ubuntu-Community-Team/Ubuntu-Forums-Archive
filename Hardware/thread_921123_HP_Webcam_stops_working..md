---
title: "HP Webcam stops working."
date: 2008-09-15
forum: Hardware
---

### Post by freedomorfire on 2008-09-15
Hi everyone. I have an HP dx6500ca laptop with an integrated webcam. Today I was trying to get VLC to record webcam streams. Because I couldn't get it to recognize the webcam properly, I tried updating the UVC drivers through subversion. 

Now my webcam doesn't work anywhere. All my programs can detect it but can't run any video feed from it. It just wont work anywhere.

This is the info I got from lsusb if that helps:

```

Bus 007 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd 
```


Any ideas guys?

---

### Post by Crafty Kisses on 2008-09-15
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by freedomorfire on 2008-09-15
i got it to work.. thanks. you can close/delete this thread.

i found out that VLC didn't support V4L2 till the newest version which isnt in the repositories yet. incase anyone wanted to know...

---

