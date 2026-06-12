---
title: "MacBook + Ubuntu or Kubuntu?"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by hindiogine on 2006-11-18
Dearest fellow Ubuntuers!

I run Kubuntu Dapper on my desktop and I am 99% happy with it.  The only complaint is that I can not make the USB drive appear anywhere (or at least I can not see it) after I stick it in the USB port.

However, this is my main question:

I am getting an Apple MacBook (not pro).

I would like to dual-boot with Linux.  So, what should I install on it?  Ubuntu or Kubuntu?   My preference is Kubuntu, but I could also use the KDE apps in GNOME.   I mostly need to use Quanta and Kyle as well as Amarok and Kaffeine.

I do have zero experience with Macs.

So, which one works better on a MacBook, Kubuntu or Ubuntu?

Any good installation guides?  The ones I have found here are only about Ubuntu, I have not found anything about Kubuntu.

Thanks,
Enrico

---

### Post by aysiu on 2006-11-18
They should be the same.

Kubuntu and Ubuntu are the same distro--same kernel, same repositories, same directory structure, same configuration files.

The only difference is the default set of applications and the default desktop environment (KDE or Gnome).

In fact, you can use *both* Kubuntu *and* Ubuntu on your Macbook. Just install Ubuntu and then paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

### Post by hindiogine on 2006-11-18
Thanks Aysiu!

I am wondering about the tools for laptop specific functions: wireless connectivity, hybernate, camera, etc.

Are these tools desktop environment specific?  E.g. better (or existing) in Ubuntu rather than Kubuntu or viceversa?

I do not have much disk space, thus, if possible, I would like to avoid installing both GNOME and KDE.

Thanks,
Enrico

---

### Post by aysiu on 2006-11-18
Well, each desktop environment has its own native tools to handle those things, but if you find one tools suits you better than another, you can always use a non-native tool (KDE tool in Gnome or vice versa).

As for disk space, when I had Xubuntu, Ubuntu, Kubuntu, and random other extra applications installed, my total Ubuntu disk use was 3.5 GB. Is your hard drive smaller than that?

---

