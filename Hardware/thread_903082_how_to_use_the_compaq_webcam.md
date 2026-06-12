---
title: "how to use the compaq webcam?"
date: 2008-08-27
forum: Hardware
---

### Post by jrecortel on 2008-08-27
hello. i installed ubuntu 8.04 on my laptop, compaq presario v3901tu. all is well except i dont know how i can use its webcam.can somebody please help me on this so i can use the built-in webcam. do i have to installed some software to use it? and if i have to install something, what is it and how can i install it?thank you.
btw, i am a new linux user. thanks again.

---

### Post by VMC on 2008-08-27
> **jrecortel said:**
> hello. i installed ubuntu 8.04 on my laptop, compaq presario v3901tu. all is well except i dont know how i can use its webcam.can somebody please help me on this so i can use the built-in webcam. do i have to installed some software to use it? and if i have to install something, what is it and how can i install it?thank you.
btw, i am a new linux user. thanks again.

It depends on what you want to use it for. One program to install is called "luvcview". Also Skype can be used to make video calls. Ekiga is already installed and you can check out the video section. Just click on the small webcam icon inside that program.

---

### Post by Crafty Kisses on 2008-08-27
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by jrecortel on 2008-08-28
i installed cheese and i can now use the webcam.also tried ekiga and also works fine.thank you.problem solved.:)

---

