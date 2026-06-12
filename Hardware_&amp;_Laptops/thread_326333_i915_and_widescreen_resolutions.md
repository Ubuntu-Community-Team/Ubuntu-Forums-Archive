---
title: "i915 and widescreen resolutions"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by waldorf on 2006-12-27
I've been working at getting a 1680x1050 external monitor to work with my laptop which uses  Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller and have not had a whole lot of luck. See [http://www.ubuntuforums.org/showthread.php?t=320815](http://www.ubuntuforums.org/showthread.php?t=320815)

It appears as if the issue is that the intel card doesn't know how to do 1680x1050. I am perfectly happy to spend a little more time trying to make it play nice (any suggestions), but I'm wondering if it is better to return the monitor I have and get something that the i915 can work with. Thoughts?

What is the highest widescreen resolution an i915 can do without having to do major hacking?

Thanks!

---

### Post by evilghost on 2006-12-27
You need to use the 915resolution package:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by waldorf on 2006-12-27
> **evilghost said:**
> You need to use the 915resolution package:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Excellent, I will give that a try - but basically it sounds like you think this is manageable. Yes?

Thanks!

---

### Post by evilghost on 2006-12-27
> **waldorf said:**
> Excellent, I will give that a try - but basically it sounds like you think this is manageable. Yes?

Thanks!

It's how I was able to do widescreen on the wife's laptop... ;)

---

### Post by bps7j on 2006-12-27
I just posted a related question here: [http://ubuntuforums.org/showthread.php?t=326211](http://ubuntuforums.org/showthread.php?t=326211)

If you get it working on the external monitor, would you please see if you can shed any light on my situation?  My monitor just says it can't display the video mode when I use 915resolution (the monitor says that, not xorg).

---

