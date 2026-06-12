---
title: "apt-get dependency problem"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by alphacrucis2 on 2009-07-27
I have a bit of a catch 22 problem.

Trying to install x264 using this ppa:

[https://launchpad.net/~freshmedia/+archive/ppa]("https://launchpad.net/~freshmedia/+archive/ppa")

I get the following problem:

```
The following packages have unmet dependencies:
  libavcodec-unstripped-52: Depends: libx264-68 (>= 1:0.svn20090710) but it is not going to be installed
```

If I try and install libx264-68 by doing a apt-get install -f I get this:

```
dpkg: error processing /var/cache/apt/archives/libx264-68_1%3a0.svn20090723-0.68~ppa1~jaunty1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libx264.so.68', which is also in package libx264-67
```


Any ideas?

---

### Post by snek on 2009-07-27
Maybe try adding the Medibuntu repositories?
In this case Medi stands for Media, not Medical (that's what I first thought hehehe)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Also I recommend to use sudo aptitude install, instead of apt-get.. It is much better at resolving dependencies.
Also, try purging the previous installed files first before trying to reinstall, seems it's not liking the fact you already have some packages installed.
Aptitude might fix this automatically, but without being able to test that I can't guarantee it.

---

### Post by alphacrucis2 on 2009-07-27
> **snek said:**
> Maybe try adding the Medibuntu repositories?
In this case Medi stands for Media, not Medical (that's what I first thought hehehe)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Also I recommend to use sudo aptitude install, instead of apt-get.. It is much better at resolving dependencies.
Also, try purging the previous installed files first before trying to reinstall, seems it's not liking the fact you already have some packages installed.
Aptitude might fix this automatically, but without being able to test that I can't guarantee it.

Thanks for the advice on aptitude. In the mean time I gave up on that PPA which seems to be problematic. I am now just using medibuntu plus kow ppa to get latest VLC and all is well.

---

