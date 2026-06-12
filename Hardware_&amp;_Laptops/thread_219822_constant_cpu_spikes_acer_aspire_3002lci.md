---
title: "constant cpu spikes acer aspire 3002lci"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by paridoth on 2006-07-20
on my acer aspire i can see a constant never ending cpu spike to 100% every 2 seconds in my cpu graph, however i dont see a program that is doing this in the system monitor, even if i change the update to every 1 secobnd, and its not long enough to increase my cpu scaling, doesn anyone know of this hapeneing? or a way to figure out what it is? or even better, a fix for it? im pretty sure this hapened in windows too, which is really odd.

---

### Post by djoelsson on 2006-07-21
Hi there,

You don't say what processor you have, but I had the same issue until the latest kernel came out.

I have a core duo that was doing the same thing.  I was using the "ondemand" speed governor.  However, the latest kernel runs fine on the "userspace" governor.

On the applet it looked like it was spending half of the time at 100%.  However, when I looked at the actual power state statistics, it was more like 10% in C2 and the rest of the time in C3, so it wasn't as bad as it looked.

Dan

---

### Post by paridoth on 2006-07-21
its an amd sempron 2800+

---

### Post by paridoth on 2006-07-22
i tried flashing my bios but but it didnt help, in windows i dont see the spikes in the system monitor, however when playing games that require all of the cpu like diablo II and such, i notice an extreme lag at the same intrevals, here is a screen shot of my cpu graph

[[IMG]http://img91.imageshack.us/img91/8109/screenshotvv5.th.png[/IMG]](http://img91.imageshack.us/img91/8109/screenshotvv5.png)

---

