---
title: "saa7130 works in 9.04 and not working in 9.10"
date: 2009-11-28
forum: Hardware
---

### Post by mphill2 on 2009-11-28
I have saa7130 tv card which worked on 9.04 if I loaded module as follows

sudo modprobe saa7134 card=52 tuner=56

After I upgraded to 9.10 card is not working. In TV application I can hear white noise and that's all.
Same thing is happening in Suse 11.2.

Help please...


EDIT:

Solved by using old kernel ... 2.6.29 instead of 31. 
Anyway seems like temporary sollution.
To me this seems like somebosy screwed up something in w4l in new kernel... or I am just stupid and missing something important.

---

