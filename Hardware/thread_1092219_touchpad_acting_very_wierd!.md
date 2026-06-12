---
title: "touchpad acting very wierd!"
date: 2009-03-10
forum: Hardware
---

### Post by lazy_bones1987 on 2009-03-10
Hey there,
I have been experiencing this strange problem with my touchpad. It used to work fine, but for the past couple of weeks, I just cant use it properly. It goes haywire when i try to move the pointer somewhere. The mouse pointer goes in a different direction most of the times, right clicks and creates folders and moves them to trash and stuff(this is what i meant by haywire)

I have Windows Vista as my primary OS and it works perfectly fine there. 
(Just telling you this so that I can eliminate doubts of something wrong with the hardware)

Just to let you know about my specs:
OS-Ubuntu 8.10
Acer 5710g
1gb ram, 2.0 GHz Centrino Duo, 140 GB HDD

---

### Post by smashagnome on 2009-03-10
One thing you can try to do is add a kernel parameter.

i8042.nomux=1

I had to do this with my DELL XPS.

See this thread [http://ubuntuforums.org/showthread.php?t=737060](http://ubuntuforums.org/showthread.php?t=737060)

regards

---

### Post by lazy_bones1987 on 2009-03-11
the solution you have pointed out would be in the case where the touchpad is not working yeah?
But mine works....it used to work fine in the beginning...just for the past couple of weeks its acting strange!

---

### Post by smashagnome on 2009-03-11
I had the exact same thing with my laptop.  It worked fine for months and then stopped working after an upgrade to the O/S.

Try it and see if it helps, if it doesnt you can always remove the grub entry.

---

