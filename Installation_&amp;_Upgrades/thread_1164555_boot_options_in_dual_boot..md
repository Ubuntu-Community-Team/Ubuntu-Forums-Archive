---
title: "boot options in dual boot."
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by joerdie on 2009-05-19
Hello all. I recently decided to dual boot my xp machine with ubuntu. Have been dual booting my mac for some time now and really love the way it all worked out. 

Installed 9.04 on its own partition yesterday and everything seems to running well. It was rather easy as I was nuking an old drive and starting with both OS's from scratch. 

The only trouble that I am having is with the startup itself. Pre-OS I am asked what OS I want to boot in what looks like bios. There is one windows coice at the bottom and 5 or so Ubuntu choices. After 10 sec. or so, Ubuntu boots automatically if I don't choose anything else. 

My question is, is there a boot loading program as on the mac that looks nice and lets me choose between the two OS's that I want to boot from? In other words, I would like two choices, Unbuntu or XP, without all of the other ways to boot Ubuntu. Also I would like the choice screen to be something... pleasant.

---

### Post by zvacet on 2009-05-20
What you see is grub and you can choose witch OS you want to but with arrow keys.Five ubuntu options are two kernels and recovery modes and memtest.It is god to have two kernels installed in case that you have problem with one you can use other.

---

### Post by lisati on 2009-05-20
> **zvacet said:**
> What you see is grub and you can choose witch OS you want to but with arrow keys.Five ubuntu options are two kernels and recovery modes and memtest.It is god to have two kernels installed in case that you have problem with one you can use other.

I concur.

BTW, "recovery mode" is roughly equivalent to Windows "safe mode" or "recovery console"

---

### Post by joerdie on 2009-05-20
Thanks for the info. Is there a way to streamline the grub interface? I am trying to get my wife involved and she wasnt that enthused. The first thing she said when she saw it was, "Looks like DOS to me."

---

### Post by Mark Phelps on 2009-05-20
You can take a look at the info linked below:

[http://grub.gibibit.com/]("http://grub.gibibit.com/")

Haven't tried this myself. Am happy with the "DOS-like" list and a background image.

---

### Post by themusicalduck on 2009-05-20
There is a program that lets you change a few things with grub called startup manager.

```
sudo apt-get install startupmanager
```

In a terminal to get it.

It won't make things look as good as the bootup manager on a mac, but you can change the text colour and put a background image up. It also lets you choose how many kernels you want listed in grub so it will look a bit neater.

---

