---
title: "version for pentium iii, 256MB RAM(ubuntu,xubuntu,dreamubuntu,redhat,...)"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by phamtuanamd on 2009-03-12
Help me! Thanks

---

### Post by taurus on 2009-03-12
Xubuntu, Puppy Linux, Damn Small Linux, etc.

---

### Post by mpsii on 2009-03-12
Try crunchbang linux (ubuntu with openbox and other desktop utilities rather than Gnome, KDE, or XFCE).

Try any of the minimalist installation documents for ubuntu.

---

### Post by snowpine on 2009-03-13
If you want to stick with the Ubuntu family, check out Crunchbang.
If you want something a little lighter and faster: DSL, Puppy, SliTaz, Antix.
Lots of good advice in this thread: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by elliotn on 2009-03-13
Well am running ubuntu 8.10 with p3 256mb without hustle

---

### Post by phamtuanamd on 2009-03-13
Thanks! I used ubuntu successfully 7.04 with LiveCD by order: all generic_ide floppy=off irqpoll, but can't access to the root,I have no ide how to access root and cannot install versions other of ubuntu( 8.04,8.10)with error message: busybox v.1.1.3. I will try to install other versions(xubuntu,puppy,...). What to ask your help!

---

### Post by mpsii on 2009-03-13
If you are talking about the root user account, it is disabled in Ubuntu.

You access your system as your user account created during install. All root functions can be accessed via the sudo command.

However, I have found that you can:

```
$ sudo su
# passwd
```

When you sudo su, you are su-ing to the root account. Then by typing passwd, you are setting a password for root. This enables the root account. I am not sure, however, whether this opens up local login or ssh login capability.

---

### Post by jespdj on 2009-03-13
I have an old laptop with an 1 GHz Pentium III with 256 MB RAM, and Xubuntu 8.10 runs very well on it.

**mpsii**: Have you read this: [New forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=716201)

You NEVER need to enable the root account on Ubuntu. With sudo you can do anything that you need to do. See this for more info: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by mister_p_1998 on 2009-03-13
Im running Xubuntu 8.04 on a Pentium 3 550 mhz with 512mb ram & a 64 mb Nvidia video card. Runs smoothly!
Steve

---

### Post by batezippi on 2010-07-20
What about Slax ?! Is it better than Xubuntu (and the other like it..)

---

### Post by cascade9 on 2010-07-20
batezippi - you would do better to create a new thread than posting on a fairly old thread like this.

---

