---
title: "Asus ux6404vi Audio Issues"
date: 2024-03-29
forum: Hardware
---

### Post by anru-an on 2024-03-29
Hey, 
I've installed 22.04 (6.5.0-26-generic) on an Asus UX6404vi and the audio is not working.

Found a post / git solution that involves a custom kernel build to add support for it, and a fix - but with that I start having linux header install and  nvidia drivers issues.

Can the support for this laptop's audio be added to a future update ?

Thanks in advance

---

### Post by #&amp;thj^% on 2024-03-29
What shows with:
```
sudo dmesg | grep CSC3551

```
Might shed some light...

---

### Post by Yellow Pasque on 2024-03-31
You're going to need at least a 6.7 kernel.
[https://github.com/torvalds/linux/commit/ae53e2198cb811f7ee7c5cd4580bf42e88086fa5](https://github.com/torvalds/linux/commit/ae53e2198cb811f7ee7c5cd4580bf42e88086fa5)

You're also going to need updated cirrus firmware: [https://gitlab.com/asus-linux/firmware/-/tree/main/cirrus](https://gitlab.com/asus-linux/firmware/-/tree/main/cirrus)

It's probably best to wait for Ubuntu 24.04 in a few weeks and install that (or just install it now, since it's close to final: [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/) )

---

