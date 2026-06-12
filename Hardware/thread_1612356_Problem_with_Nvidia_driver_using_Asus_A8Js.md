---
title: "Problem with Nvidia driver using Asus A8Js"
date: 2010-11-03
forum: Hardware
---

### Post by blaszta on 2010-11-03
Last week I upgrade my system to Ubuntu 10.10 and everything works fine (the last time I do clean install I think 9.04), until yesterday when I update the Nvidia proprietary driver.
Now the desktop not rendered properly, some pixel and color misplaced, make the system slow and unusable after period of time.

[IMG]http://i53.tinypic.com/t89ge1.png[/IMG]

[IMG]http://i54.tinypic.com/2dufe60.png[/IMG]

I try to use different driver (not nvidia-current) but the problem still exist.

I do clean install of 10.10 and 10.04, but found the problem still exist.

Is there a way I can use the 9.04 (or 9.10) nvidia driver in 10.10?

Btw, the notebook (Asus A8Js) use GeForce Go 7700 if it helps.

---

### Post by blaszta on 2010-11-03
Update: I manage to make it work by reducing the color depth to 16 in xorg.conf. Although I'm not quite satisfied with this solution since I know it works with 24 bit color depth before.

Anybody else have better solution?

---

