---
title: "Screen flickering on low battery level"
date: 2016-07-23
forum: Hardware
---

### Post by magicleon on 2016-07-23
Hi everybody,
I'm an old Debian user and wanted to try Ubuntu, so i've recently installed Kubuntu 16.04 LTS (with KDE Plasma 5) on my Asus laptop.

Some days ago I tried to install nVidia drivers but nothing came up,  so I reverted (or I guess so) to the "original" situation. Everything  works fine (actually I don't neet my card, integrated graphics works  fine for me now). I've only one issue... when battery is low (20% and lower) my screen  starts flickering bad when opening "new graphic elements"... What can it  be? When battery is above 20% (or so) I have no flickering at all, same when  plugged to AC (even if battery level is low) 


  The command ```
glxinfo|egrep "OpenGL vendor|OpenGL renderer*"
``` gives this back:

  ```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
     

```

My laptop is an Asus X555LD.
I don't know if this is the right section to post this thread, so i'm sorry if I'm wrong.
Thanks in advance!

---

### Post by magicleon on 2016-07-23
Today I installed Bumblebee and everything went back to normal. I don't know why but it works lol

---

### Post by QDR06VV9 on 2016-07-23
Hey that is good to hear you have found a solution.
And if you would could you now mark your thread as Solved using the thread tools (Upper right hand corner title bar)
It may help future visitors with same problem.
Thanks and glad you got it sorted out.
Kind Regards

---

### Post by magicleon on 2016-07-23
Oh yeah I'm sorry. Done!

---

