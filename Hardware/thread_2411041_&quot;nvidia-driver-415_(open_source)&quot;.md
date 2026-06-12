---
title: "&quot;nvidia-driver-415 (open source)&quot;?"
date: 2019-01-23
forum: Hardware
---

### Post by heydihoe on 2019-01-23
Hey everyone,

This is my first post on Ubuntu forums so go easy on me if I am not posting correctly.

I am running a Nvidia Geforce GTX 1080 in my Ubuntu 18.04 system.

When I open up the Software & Updates program, it states that I have the restricted repository enabled. But when I switch to the Additional Drivers tab it states that I have enabled "Using NVIDIA driver metapackage from nvidia-driver 415 (open source)".

I have installed Ubuntu a couple of times and this is the only time that it has stated that that package is open source.

Isn't the nvidia-driver-415 metapackage suppose to be closed source from NVIDIA themselves and the Nouveau display driver is suppose to be open source? I would prefer the closed source driver installed. Do I have the right package installed?

Thank you, in advance. :)

---

### Post by mc4man on 2019-01-23
I would suspect you have the [graphics-drivers ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") enabled. (nvidia-410 and 415 aren't available in the standard Ubuntu repos
If so then  all of their drivers show up as " (open source)", why no idea but certainly not the case.. (as far as the drivers source, maybe the metapackage itself is 'open source' ??

---

### Post by Autodave on 2019-01-24
You have the right package installed.  I am assuming that everything is working OK?

---

