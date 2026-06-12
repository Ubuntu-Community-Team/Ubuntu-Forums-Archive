---
title: "Cannot activate Desktop Effects with Intel Graphics Card"
date: 2011-01-27
forum: Hardware
---

### Post by nirvana06 on 2011-01-27
Hi

I have the latest Ubuntu version and have been trying to enable compiz also when i try to do so, i receive a message saying that "could not be activated". When i type lspci -nnk | grep VGA for the graphics card i get:

00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)

I made alot of research on how to get Intel graphics work on Ubuntu, but couldnt find any solution

Would be grateful if you can help me..[IMG]http://forums.fedoraforum.org//forum/images/smilies/confused.gif[/IMG]

---

### Post by coffeecat on 2011-01-27
By latest version I presume you mean Maverick. If so, have a look here:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

As you can see you have a choice between 2d only and a stable system or 3d and compiz and the likelihood of lockups.

Unfortunately, the 8** series of Intel graphics are getting very old now and the situation is not likely to get better.

---

