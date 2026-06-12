---
title: "nVidia 6150LE startup resolution problem"
date: 2009-10-18
forum: Hardware
---

### Post by sandzofpersia92 on 2009-10-18
Whenever I startup Ubuntu my screen resolution keeps changing to 800 X 600, but my actual screen size is 1280 X 1024 and it never stays that way. Everytime it starts up I have to manually switch it to 1280 X 1024 through the nVidia control panel and its getting pretty annoying. So far I find Ubuntu very appealing and very useful, but its just this problem, other than this everything is awesome!:KS

---

### Post by Its_Mr_to_you_sonny! on 2009-11-15
I've had a similar problem since upgrading to 9.10.  I found the answer in another thread here, that I now can't find.  

Check; /home/<username/.config/monitors.xml, mine had the following entries:

<width>800</width>
<height>600</height>
<rate>61</rate>

Setting these to the correct values for my monitor fixed the problem.

---

