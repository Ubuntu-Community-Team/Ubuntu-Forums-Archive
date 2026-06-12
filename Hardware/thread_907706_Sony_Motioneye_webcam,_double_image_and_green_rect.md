---
title: "Sony Motioneye webcam, double image and green rectangle"
date: 2008-09-01
forum: Hardware
---

### Post by frunns on 2008-09-01
Ok, so here's the deal. I'm using my webcam on Skype, which works perfectly fine (except for it filling up my log-files, but that's a different matter). But, when I want to use it on Cheese (or like the Multimedia Systems Selector) I get an image like the attached file. Two images from the capture device next to each other and below them a big, green rectangle. Anyone got any clue on how to solve this?

---

### Post by IntuitiveNipple on 2008-09-01
Cheese doesn't properly support many video formats (chromas) as has been discovered by a lot of users recently.

I seem to be one of the 'lucky' ones (although I can't see the point of cheese) in that it is too scared of me to misbehave with the V4L2 r5u870-dkms driven Motion Eye on my Vaio :)

---

### Post by frunns on 2008-09-02
If only my cheese was scared of me... :(

---

### Post by IntuitiveNipple on 2008-09-02
> **frunns said:**
> If only my cheese was scared of me... :(
I bet it's scared of your mouse, though :p

---

### Post by Crafty Kisses on 2008-09-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by frunns on 2008-09-14
Yeah, Ekiga's working just fine... So, Skype and Ekiga can use the cam, but not Cheese. Bah.

---

