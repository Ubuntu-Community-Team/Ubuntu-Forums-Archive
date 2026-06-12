---
title: "installing 180.29 drivers"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by troegs on 2009-02-14
I am attempting to install the latest nvidia drivers but the site I am looking at for a how-to had this following line:

"Please note that the Linux kernel headers and a GCC compiler will be required to complete the installation!"

As I am fairly new to linux I don't know what these means. how do I know if I have these? if I don't where do I find them? 

thanks for any help anyone can offer.

T.

---

### Post by troegs on 2009-02-14
Okay. so I see that the GCC is the Gnu c compiler, which I can see I have after looking at the synaptic package manager. what is meant by the other part of the statement? Linux kernel header?

---

### Post by frost151n on 2009-02-14
Isn't Linux Kernal Headers installed by default. 
I saw it in a update once.

---

### Post by cb951303 on 2009-02-14
there is a PPA repo for 180.29: [https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

---

### Post by dorkdork777 on 2009-02-14
Newbie to installing drivers here.

I've added that, but I'm kind of confused as to how to install. Do I just install nvidia-glx-180, and the rest is automagic? Or is there more that I need to do to prepare it for use?

EDIT: Sorry, worked it out.

I installed "nvidia-glx-180" and "nvidia-180-modaliases", and ran the NVIDIA settings utility. It told me I had to run a command; I ran it, it did some stuff, then when I restarted X it worked :)

---

