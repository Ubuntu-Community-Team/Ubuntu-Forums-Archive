---
title: "ubuntu causing burn-in (but Windows doesn't)"
date: 2012-08-08
forum: Hardware
---

### Post by nrundy on 2012-08-08
Got two laptops, identical models. I got Windows 7 on one, Ubuntu on the other.

One thing I've noticed is that the one with Ubuntu always suffers from burn-in on the LCD screen (I thought LCDs were immune to this, but apparently not). The Windows install never has burn-in. I thought maybe it was a hardware thing (although both computers are identical) so I installed ubuntu onto the computer with Windows 7. Sure enough after use, I start to see burn-in.

Why is Ubuntu causing burn-in when Windows does not and is there a way to stop ubuntu from causing burn-in on the LCD screen? I can "repair" the burn-in by opening Gedit, pressing F11 and then letting this empty white page sit on the screen for an hour or so. But why does Ubuntu cause burn-in when Windows does not for identical use scenarios?

---

### Post by ajgreeny on 2012-08-08
Are you sure this is burn-in and not an artifact of your graphic card and driver?

Surely burn-in is permanent, not something that goes after the kind of action you mention.  What card and driver are you using?

---

### Post by nrundy on 2012-08-09
not all burn-in is permanent, especially if it isn't left on screen for days and days. Using a white screen can rememdy burn-in that is present but hasn't gotten to the permanent stage yet.

using Intel integrated graphics, same as on my Windows computer.

---

### Post by Mark Phelps on 2012-08-09
Actually .. screen burn-in IS permanent ... see below:

> Screen burn-in, image burn-in or ghost image, colloquially known as screen burn or screen afterimage, is a _permanent _discoloration of areas on an electronic display such as a cathode ray tube (CRT) display or computer display monitor or television set caused by cumulative non-uniform usage of the pixels.

What you're seeing is a ghost after-image, which is NOT permanent, and does not damage the screen.

---

### Post by alan21276 on 2012-08-09
I've noticed this too.

Especially with the tabs on Google Chrome.

A display driver issue perhaps?

---

### Post by nrundy on 2012-08-10
> **Mark Phelps said:**
> Actually .. screen burn-in IS permanent ... see below:



What you're seeing is a ghost after-image, which is NOT permanent, and does not damage the screen.

The "ghost after-image" continues to show even after reboots. So I consider it Burn-In. If you do more searching on the internet, you will find that Burn-In does occur even when it can be fixed/removed. Although there is a point where Burn-In can become truly permanent.

Perhaps it is an Intel graphics driver problem on Linux that doesn't affect the Windows driver. Anyone know where a bug report can be filed for this as it affects the Intel Linux graphics driver? I'm assuming Launchpad isn't the place for this.

---

