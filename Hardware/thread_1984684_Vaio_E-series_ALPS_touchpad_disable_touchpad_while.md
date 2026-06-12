---
title: "Vaio E-series ALPS touchpad disable touchpad while typing"
date: 2012-05-22
forum: Hardware
---

### Post by .Jonathan. on 2012-05-22
Hi, 

I have a vaio EB4Z1E with an ALPS touchpad. After installing 12.04 the 'disable touchpad while typing'-function worked out of the box. But now all of a sudden it stopped working!

The box in touchpad-settings is still checked...

Any ideas?

Thanks

---

### Post by dturvene on 2012-06-14
> **.Jonathan. said:**
> Hi, 

I have a vaio EB4Z1E with an ALPS touchpad. After installing 12.04 the 'disable touchpad while typing'-function worked out of the box. But now all of a sudden it stopped working!

The box in touchpad-settings is still checked...

Any ideas?

Thanks
See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238)

It looks to me like a new ALPS touchpad protocol that hasn't been decoded yet.  There are a bunch of diagnostics in the bug thread that can be run to verify if this is your problem.

---

