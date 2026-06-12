---
title: "Laptop shut down"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Amit Malina on 2008-01-05
Hi there, 


[SIZE="4"]When i'm using KDE with ubuntu 7.10 after a while my laptop is become very hot and it shut down.It seems that the shut down process is coming from linux because it seems like an order one.

It dosen't happening  using GNOM env.... 

anyone have an idea what is going on ?
 
Thanks 
Amit.
[/SIZE]

---

### Post by jespdj on 2008-01-05
Why are you using [SIZE="5"]such a big font[/SIZE]?

Many laptops have a built-in mechanism to shut down if (part of) the system gets too hot. It looks like you have something running that makes maybe the CPU or the graphics card work very hard all the time, which makes the laptop get too hot.

Check with the command **top** if there are processes that take up a lot of CPU time (is your CPU constantly running near 100%?).

---

