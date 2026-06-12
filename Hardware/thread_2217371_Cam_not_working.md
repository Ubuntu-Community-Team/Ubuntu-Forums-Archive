---
title: "Cam not working"
date: 2014-04-17
forum: Hardware
---

### Post by salmichaels on 2014-04-17
Running 13.04 on ASUS W5F notebook. It has a rotating cam embedded/mounted above the screen, and it and as far as I can tell the system and it aren't talking at all. It's a 1.3M cam. Not essential for me, but would love if it worked. 

Thanks!

---

### Post by coldraven on 2014-04-17
Some cameras seem to have an "Auto level" setting that in a normally lit room result in just a black output.
You can test this by installing Cheese (in the Software Centre) and then shine a flashlight at the camera. If you can then see something install "uvcview".
```
sudo apt-get install uvcview
```
 Quit Cheese, run uvcview, uncheck the "Auto level" box and adjust the Brightness slider. Then quit, no need to save anything and try Cheese again.

---

### Post by salmichaels on 2014-04-23
Tried this out, didn't have any luck. I did try to take a pic in Cheese, and I saw that funny array of green and green lines. I'm wondering if the cam might be dead in the first place. 

I tried to install ucview but the terminal said the packages weren't found.

---

### Post by mastablasta on 2014-04-24
because it's uvcview not ucview

package could also be found in software center or synaptic package manager.

---

### Post by mörgæs on 2014-04-24
13.04 is obsolete. As a first step I recommend a clean install of 14.04.

---

### Post by Geoff_Lane on 2014-04-27
Initially a friend of mine got this regarding a webcam read out;

lsmod | grep videodev

  107508  3 uvcvideo,videobuf2_core

Now since upgrading to 14.04 that command finds nothing :(

---

### Post by mörgæs on 2014-04-28
An upgrade brings along old (and possibly wrong) config files and should be avioded. A fresh install is preferred.

---

