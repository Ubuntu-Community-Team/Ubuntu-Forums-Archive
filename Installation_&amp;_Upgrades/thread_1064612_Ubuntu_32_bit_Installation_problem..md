---
title: "Ubuntu 32 bit Installation problem."
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by crux12 on 2009-02-09
I downloaded the 32 bit version of ubuntu from their site. I then mounted it with magic ISO (have no cd drive) and installed ubuntu.

Well, after it was installed, I found out it was the 64 bit verson.

I have tried this about 3 times and it's always the same result.

I'm currently using Windows XP.

---

### Post by glotz on 2009-02-09
Where did you download exactly? What was the filename? How did you figure out it was the 64 bit version?

---

### Post by crux12 on 2009-02-09
I got it from:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

The file was:

ubuntu-8.10-desktop-i386.iso

I found out it was the 64 bit version when I tried to get Flash Player working, i kept getting the error "Wrong architecture i386"

Here's my computer's specs if this helps:

CPU: AMD Athlon 64 x2 6000+
RAM: 2GB 800MHZ Patriot
GPU: hd 4850
MB:  m2r32-MVP

---

### Post by crux12 on 2009-02-09
It seems as though I'm not the only one with this problem, if anyone has found a fix for this, please share it.

This is overwhelmingly frustrating.

---

### Post by boof1988 on 2009-02-09
> **crux12 said:**
> The file was:

ubuntu-8.10-desktop-i386.iso

Can you do an md5sum of the iso file?

If it is the 32-bit file, I believe, that the md5sum should correspond to the following 32-bit md5sum.  The 64-bit md5sum is included as well.

```

f9cdb7e9ad85263dde17f8fc81a6305b *ubuntu-8.10-desktop-amd64.iso
24ea1163ea6c9f5dae77de8c49ee7c03 *ubuntu-8.10-desktop-i386.iso
```

> **crux12 said:**
> I found out it was the 64 bit version when I tried to get Flash Player working, i kept getting the error "Wrong architecture i386"

I have seen this same error in the past.  Can't figure out if the error is saying that the existing (installed) OS is i386 (32-bit) or if the software to be installed is 32-bit.  I hope someone can clarify this.

---

### Post by Taigen on 2009-02-09
I am having same problem except I havent installed anything yet. I basically looked at my firefox version number and noticed that many of my programs are saying 64 when all my friends's ubuntu doesnt. 

Firefox Version:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.5) Gecko/2008121623 Ubuntu/8.10 (intrepid) Firefox/3.0.5

---

### Post by Taigen on 2009-02-09
Does anyone know of a solution to this problem or can point me to direction to a solution, I need to get this fixed asap

---

### Post by oldos2er on 2009-02-10
64-bit Flash for Linux is here: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

---

### Post by boof1988 on 2009-02-10
> **Taigen said:**
> Does anyone know of a solution to this problem or can point me to direction to a solution, I need to get this fixed asap

Please consider waiting ~24hours before bumping a thread for your benefit.  That it the courteous way to do it.  Many people on this site want their issue fixed "asap" as well, but that doesn't mean that everyone should bump the threads in 8hours.

Also, in your specific case, next time (or this time also) consider starting your own thread so that you can get help tailored to your needs.

---

