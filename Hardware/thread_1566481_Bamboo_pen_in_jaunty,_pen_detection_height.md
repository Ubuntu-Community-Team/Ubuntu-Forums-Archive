---
title: "Bamboo pen in jaunty, pen detection height"
date: 2010-09-02
forum: Hardware
---

### Post by pardesi on 2010-09-02
I installed Bamboo pen drivers today on my jaunty. It did not work out of the box as stated in the [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom). I used the instructions given at a couple of threads and finally got it 'working'. 

The system detects the pen and the active area represents the monitor screen perfectly but, the pen treats the area 3mm or so above the pad as the pas itself that is even when i am 3mm or so away things start getting selected automatically, they start moving as if i am selecting and dragging them. When i use Xournal even when i write or just put my pen 3mm away from the pad it starts scribbling( due to the random motion of hand) it would be of great help if someone could tell me how i could adjust this zero level right. Hope i was clear.

---

### Post by Favux on 2010-09-02
It sounds like you may need: 
```
TPCButton "on"
```
either as an Option in the 10-wacom.conf or as an xsetwacom command (as part of a script for the stylus)

---

