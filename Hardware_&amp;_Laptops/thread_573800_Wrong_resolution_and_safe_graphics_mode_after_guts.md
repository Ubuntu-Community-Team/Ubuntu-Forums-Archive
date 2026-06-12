---
title: "Wrong resolution and safe graphics mode after gutsy release candidate upgrade"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by climatewarrior on 2007-10-12
Hi, Guys!

I just upgraded to Gutsy Release Candidate on my laptop and it went perfectly well. Im really excited about this new release.

The only problem that I encuntered is that it seems gutsy couldnt configure my video card correctly :(

It used to work flawlessy in Feisty. When I log in X fails to start and the new fail safe configurations come into play, great feature by the way,  and gutsy tells me its in safe graphics mode.

I included my current settings my current xorg.conf and my video card model.

Does anyone know how to configure it properly? 

Any help is appreciated. 

Bye!


Intel 82852/855GM Integrated Graphics Device

Screen and Graphics Preferences- 

Graphics Card- i810 (intel85x)

Screen 1- unknown

---

### Post by renzokuken on 2007-10-12
run ```
sudo dpkg-reconfigure xserver-xorg
``` to change xorg settings easily

---

### Post by climatewarrior on 2007-10-12
Thanks! configuring xorg with that and later adjusting resoulution with the gui tool fixed it. Thanks!

btw Ichigo Rocks!

---

