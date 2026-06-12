---
title: "Update graphics card"
date: 2018-08-06
forum: Hardware
---

### Post by toyson on 2018-08-06
hello, how do i install or update the graphics card of my intel gma4500..:P

---

### Post by slickymaster on 2018-08-06
*Thread moved to **Hardware**.*

---

### Post by pqwoerituytrueiwoq on 2018-08-06
that That looks to me a moble GPU, so i would guess you are using a laptop
given that is a quite a old chip (~10 years), if you want to upgrade that it is going to mean a new laptop

now if you actually mean the driver, any even remotely recent version of ubuntu should have the latest driver, unless it has been dropped entirely

---

### Post by toyson on 2018-08-06
Okay thanks

---

### Post by toyson on 2018-08-08
Still not solved.

---

### Post by QIII on 2018-08-08
What release of Ubuntu are you using?

---

### Post by deltamind on 2018-08-08
What exactly did you do by now to solve the problem? So that I can suggest you some solutions.

---

### Post by toyson on 2018-08-08
@ QIII i am using xubuntu 16.04

---

### Post by toyson on 2018-08-08
@ deltamind i tried using the intel graphic driver update utility but it gave an error at the end, i also tried updating xorg but it froze my system after restart.

---

### Post by springshades on 2018-08-08
I looked up some stuff. While you theoretically should be able to install the graphics drivers from the Intel site manually, I think you're likely to get stuck in dependency hell.

Instead, I think the easiest way for you to get the newest drivers is to upgrade from Ubuntu 16.04 to 18.04. The 18.04 release has the newest driver release installed.

Note that even though this will upgrade your Intel GPU driver, it's unlikely it will have much of an effect on your card. The GMA 4500 is very old, and it's unlikely that any of Intel's driver updates have focused on that card. I could be wrong. Maybe they found a serious bug at some point.

---

### Post by toyson on 2018-08-09
thanks @springshades i switched to xubuntu 18.04 late last month but after a while of usage i decided to install steam which i did  through the software store, but i noticed that when i try to run it,steam doesnt start. I would just hope that there would be an upgrade

---

### Post by springshades on 2018-08-09
Ubuntu 18.04 has the version of the Intel driver that is listed as the newest one on Intel's site.

Perhaps if you're already running 18.04 right now (in a previous post you said you were running 16.04), the new graphic driver is actually what broke things for you. In that case, you might be better off downgrading rather than upgrading. That sounds counter-intuitive, but it's actually common for older GPUs.

Also, if Steam itself won't start instead of a game it might be something else. The steam program itself is 2D, so it's unlikely to crash because of a graphics issue unless it actually gave you an error that made you think it was the GPU.

---

