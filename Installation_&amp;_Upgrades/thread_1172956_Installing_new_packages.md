---
title: "Installing new packages"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Dhananjaymb on 2009-05-29
I am new ubuntu and i dont have a internet connection at home. i install new packages in system by downloading from a public computer and installing. Is there any way to get the dependencies cleared easily?

---

### Post by Partyboi2 on 2009-05-29
Hi, you can use a program called [[COLOR=Blue]keyrx[/COLOR]]("http://keryxproject.org/") to install packages and their dependencies.

---

### Post by ActiveFrost on 2009-05-29
> **Partyboi2 said:**
> Hi, you can use a program called [[COLOR=Blue]keyrx[/COLOR]]("http://keryxproject.org/") to install packages and their dependencies.

Can it create a CD/DVD from already existing packages in cache folder ( /var/cache/apt/archives/ ) ?

---

### Post by Partyboi2 on 2009-05-29
> **ActiveFrost said:**
> Can it create a CD/DVD from already existing packages in cache folder ( /var/cache/apt/archives/ ) ?
If you are wanting to create a cd/dvd with existing packages you can use aptoncd.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by ActiveFrost on 2009-05-29
> **Partyboi2 said:**
> If you are wanting to create a cd/dvd with existing packages you can use aptoncd.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I've already tried it, but - there's a small problem ! It crashes on large files ( for example, Eclipse causes aptoncd to crash without completing the process ).
Also, if I manually add ffmpeg & x264 ( made with checkinstall ), it'll create a CD which can't be launched ( error ).

---

