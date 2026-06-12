---
title: "tv-out screen size/resolution"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by mlwalla on 2008-02-02
I recently got tv out working on gutsy gibbon using 'nvidia-settings' but I've got one small problem.  There's about a half inch black band around on the left and right sides of the screen.  I've got an nvidia geforce2go.

Is there a way to get the whole screen?  In another post, someone mentioned the TVoverscan option in xorg.conf, but the nvidia driver FAQ says that option is only available for nvidia GeForce4 and above...I suppose I could try that anyway, but does anyone know a different/better workaround?

---

### Post by dmiller40 on 2008-02-02
having the same problem here. I installed the restricted drivers and it added 1024x768 res but still left a black frame. i tried selecting a different driver to see how that would work now my computer boot in low graphics mode using the vesa driver. i go to change it but it never changes just stays at vesa. i uninstalled and reinstalled through restricted drivers but it is still using the vesa driver.

argh!
dm

---

### Post by dmiller40 on 2008-02-07
bump... still cant get my nvidia driver enabled.

dm

---

### Post by oldsoundguy on 2008-02-08
try using Envy to install the drivers .. worked for me on three Gutsy boxes.

---

### Post by dmiller40 on 2008-02-08
OK got envy installed and ran, completed and restarted twice. I go to screen & graphic -> graphics card still says vesa.  the restricted drivers says nvidia accelerated graphics driver not in use. And when i got to system tools -> nvidia settings i get "you do not aprear to be using the nvidia x driver. please edit your x configuration file (just run `nvidia-xconfig` as root) and restart the server."

i have ran 
sudo nvidia-xconfig

and restarted and still get the same message.
thanks

dm

---

### Post by oldsoundguy on 2008-02-08
what happens if you go to system> preferences> screen resolution?  I set mine there (and also rotated them to portrait)

---

### Post by dmiller40 on 2008-02-08
Ok finally got the driver back with Envy, but still have the black frame around the screen. I have it set as the highest resolution. I had someone mention tv overscan. has any1 else done this.

dm

---

### Post by oldsoundguy on 2008-02-08
are there PHYSICAL adjustment buttons on the monitor?  I have them on ALL of my monitors (all are LCD)

---

### Post by dmiller40 on 2008-02-08
I got it fixed. I have my 50" plasma hooked up by s-video. I just had to go to my nvidia settings and change my overscan from 8 to 14. Thanks for your help

dm

---

