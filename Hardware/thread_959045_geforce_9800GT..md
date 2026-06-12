---
title: "geforce 9800GT."
date: 2008-10-26
forum: Hardware
---

### Post by a Dalmatian on 2008-10-26
Ok I sure the problems that I'm having can be solved once this taken care of, but how the heck do I install the drivers for this thing? (if you need anymore information to help me, please kindly tell me and I will provided it)

---

### Post by jocko on 2008-10-26
> **a Dalmatian said:**
> Ok I sure the problems that I'm having can be solved once this taken care of, but how the heck do I install the drivers for this thing? (if you need anymore information to help me, please kindly tell me and I will provided it)

Which release of ubuntu do you use?

In Hardy (8.04), the normal restricted driver in the repos is too old to support that card, so you will have to install a newer version.
The simplest way is to install the package envyng-gtk, then use envyng to install the correct driver.

From a terminal:
```
sudo apt-get install envyng-gtk
gksudo envyng -g
```
I've never used envyng myself, but I think it should be quite self-explanatory once you get it running. Otherwise there are lots of people on the forums that know how to help you.

In intrepid (8.10, which will be released in a few days), the restricted driver supports your card, so it is best installed from the restricted driver manager (System --> Administration --> Hardware Drivers).

Good luck

---

### Post by a Dalmatian on 2008-10-26
> **jocko said:**
> Which release of ubuntu do you use?

In Hardy (8.04), the normal restricted driver in the repos is too old to support that card, so you will have to install a newer version.
The simplest way is to install the package envyng-gtk, then use envyng to install the correct driver.

From a terminal:
```
sudo apt-get install envyng-gtk
gksudo envyng -g
```
I've never used envyng myself, but I think it should be quite self-explanatory once you get it running. Otherwise there are lots of people on the forums that know how to help you.

In intrepid (8.10, which will be released in a few days), the restricted driver supports your card, so it is best installed from the restricted driver manager (System --> Administration --> Hardware Drivers).

Good luck

I think just gota wait for it then, dang.

---

