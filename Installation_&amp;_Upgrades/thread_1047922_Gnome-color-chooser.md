---
title: "Gnome-color-chooser"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by themagicmanfromtrent on 2009-01-22
I'm really struggling to find a way to install the gnome colour chooser as i can't seem to find the right dependencies.

I keep getting errors such as this:

```
danny@DAN:~/Desktop/gnome-color-chooser-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

Anyone have any idea which packages i'm missing, or if there's a way to just get them all in one go? Build-install doesn't work.

---

### Post by Partyboi2 on 2009-01-22
Have you got build-essential package installed?
```
sudo apt-get install build-essential
```

---

### Post by themagicmanfromtrent on 2009-01-22
> **Partyboi2 said:**
> Have you got build-essential package installed?
```
sudo apt-get install build-essential
```

Okay, that's wierd. I'm pretty sure I tried that. :S

Thanks!

---

