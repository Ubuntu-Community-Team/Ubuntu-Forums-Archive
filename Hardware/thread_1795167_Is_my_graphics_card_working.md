---
title: "Is my graphics card working?"
date: 2011-07-02
forum: Hardware
---

### Post by evilbrent on 2011-07-02
> brent@doris:/dev/dri$ lspci
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

I've just installed Ubuntu 11 on a computer with this graphics controller, which I've googled and it _seems_ like it should be able to do ok video (I don't really know what I'm looking for).

I can only get 1024 x 768 (4:3) resolution and video is really very pixellated. I'm using this computer on a 47" telly so you can imagine I'd love to get better graphics if my machine can do it.

So - does anyone know how I can find out how I can find out what graphics I'm capable of? And if the card is capable of better than i'm getting can I install drivers or something?

---

### Post by sanderd17 on 2011-07-02
This is a second generation i3/5/7?

I believe the best drivers aren't yet in the kernel. The first thing I would try is to get the newest kernel (the 3.0 beta) and see if it works.

I have a first generation i3, and I can certainly go to 1600x900 (the screen maximum).

---

### Post by sanderd17 on 2011-07-02
you can get the kernels from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc5-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc5-oneiric/)

first you need to install linux-headers-*-all.deb, then linux-headers-*-generic-*.deb and finally linux-image-*.deb.

---

### Post by evilbrent on 2011-07-02
cool thanks. My friend gave me this machine about 3 years ago, so I'm guessing it's a first generation...

so stupid question: i just click on the links??

---

### Post by sanderd17 on 2011-07-02
> **evilbrent said:**
> cool thanks. My friend gave me this machine about 3 years ago, so I'm guessing it's a first generation...


3 years ago, than it's not an i3/5/7, installing a new kernel won't work. Sorry

I'll look if I find anything better.

---

### Post by sanderd17 on 2011-07-02
Aha, it seems that Paha had the same problem and also a sollution for it: [http://ubuntuforums.org/showthread.php?t=1756490](http://ubuntuforums.org/showthread.php?t=1756490)

---

### Post by evilbrent on 2011-07-02
sweet!

thanks heaps. I'll mark this thread as solved then, and start a new one if I need to try to get help understanding what on earth [paha77]("http://ubuntuforums.org/member.php?u=1231816") is talking about :D

Cheers.

---

