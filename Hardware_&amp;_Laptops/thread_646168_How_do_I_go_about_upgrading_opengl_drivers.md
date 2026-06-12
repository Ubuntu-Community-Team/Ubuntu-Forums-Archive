---
title: "How do I go about upgrading opengl drivers?"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by Drethon on 2007-12-20
I'm new to linux, I have a program I'm trying to run that is all compatible except the opengl drivers for my graphics card.  Where do I start looking in linux to track down how to upgrade my graphic card drivers?

---

### Post by K.Mandla on 2007-12-21
What kind of graphics card is it? Newer Nvidia cards need the [nvidia-glx-new]("http://packages.ubuntu.com/nvidia-glx-new") package, but older ones use [nvidia-glx]("http://packages.ubuntu.com/nvidia-glx") or [nvidia-glx-legacy]("http://packages.ubuntu.com/nvidia-glx-legacy"), depending on the model.

ATI and other cards have corresponding packages as well.

---

### Post by Drethon on 2007-12-21
The graphics board on this laptop is an intell chipset.  Listed on the order form as a INTELPRO/WL3945ABGUSCNLAAP.

---

