---
title: "Reinstalling Nvidia 190.53"
date: 2010-01-16
forum: Hardware
---

### Post by emoguitarist06 on 2010-01-16
I'm running 32bit Ubuntu 9.10 on my Compaq Presario CQ50 with a Nvidia Geforce 800M graphics card.

I have installed the Nvidia driver from their website
NVIDIA-Linux-x86-190.53-pkg1.run

But I find that everytime there is a Kernel update in Karmic that my screen flickers. And so I restart my computer and then the Nvidia Driver is no longer working So I run this code

```
sudo /etc/init.d/gdm stop
cd Downloads
sudo sh ./NVIDIA-Linux-x86-190.53-pkg1
```

And I basically have to reinstall the Nvidia Driver every time there is a kernel update.

Does anyone else have this problem?

---

### Post by mörgæs on 2010-01-16
This is normal. A screen driver that one adds manually is lost when the kernel is updated.

---

### Post by emoguitarist06 on 2010-01-16
> **mörgæs said:**
> This is normal. A screen driver that one adds manually is lost when the kernel is updated.

oh ok.

that sucks :(

---

### Post by mörgæs on 2010-01-18
I would say it is a minor annoyance. 

A new kernel is not an everyday event, and running the necessary commands only takes a few seconds.

---

