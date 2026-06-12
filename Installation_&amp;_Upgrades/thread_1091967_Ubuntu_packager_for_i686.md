---
title: "Ubuntu packager for i686"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Neo_The_User on 2009-03-09
Hi. Ever notice that every single package except for Libc6 (yeah and like 2 other apps) are all i386 optimized? Well I was wondering, what application would I use to package applications from source, turn them into i686 packages then compress them to .deb so I can check for dependency problems? I'm doing some experimenting with 8.10 and messing around with X11, how would I go about installing from source without doing sudo make install? I broke my system twice today compiling apps from source. Also, compiling gcc 4.4 from source messed my whole system up and HAL and Dbus wouldn't even start on boot.

Disregard the gcc thing. I made a new thread.

---

### Post by Chemical Imbalance on 2009-03-09
> **Neo_The_User said:**
> Hi. Ever notice that every single package except for Libc6 (yeah and like 2 other apps) are all i386 optimized? Well I was wondering, what application would I use to package applications from source, turn them into i686 packages then compress them to .deb so I can check for dependency problems? I'm doing some experimenting with 8.10 and messing around with X11, how would I go about installing from source without doing sudo make install? I broke my system twice today compiling apps from source. Also, compiling gcc 4.4 from source messed my whole system up and HAL and Dbus wouldn't even start on boot.

i686 is not X86-64 
It is basically an optimized i386
[http://en.wikipedia.org/wiki/Intel_P6_(microarchitecture)](http://en.wikipedia.org/wiki/Intel_P6_(microarchitecture))

Unless you already know this of course :)

(I'm assuming-wrongly?-that you want 64-bit)

Haha just ignore my post then :)

---

### Post by Neo_The_User on 2009-03-09
> **Chemical Imbalance said:**
> i686 is not X64 

[http://en.wikipedia.org/wiki/Intel_P6_(microarchitecture](http://en.wikipedia.org/wiki/Intel_P6_(microarchitecture))

I know. I know the difference between i386, i686, and AMD64. There is also i486 and i586.

---

### Post by Chemical Imbalance on 2009-03-09
> **Neo_The_User said:**
> I know. I know the difference between i386, i686, and AMD64. There is also i486 and i586.

Sorry! :) See my edited post above ;)

Sometimes I don't think before i post

---

### Post by Neo_The_User on 2009-03-09
My processor doesn't support 64-bit arcitecture. i686 is 32-bit. It's fine don't worry about it. Does checkinstall always build a package as i386 or no? I never successfully created a deb package that was i686 optimized. Not even sure if it's possible.

Next question still remains unanswered. When I compiled gcc 4.4 from source (compiled to i686 X86 32-bit arcitecture) HAL, Dbus, networking, almost everything broke. I re-installed (I have no problem doing so any day, any time) and it fixed it but now I want to compile gcc 4.3 this time but still compile as i686 X86 32-bit arcitecture. And my English dictoionary suggestions just disapperead.

---

### Post by Chemical Imbalance on 2009-03-09
> **Neo_The_User said:**
> My processor doesn't support 64-bit arcitecture. i686 is 32-bit. It's fine don't worry about it. Does checkinstall always build a package as i386 or no>

I know, I just glazed over the first sentence and assumed...

This might help: [http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)
and this: [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by Neo_The_User on 2009-03-09
Thanks. About gcc... or would that be a new thread? btw my dictionary came back after a reboot.

---

### Post by cariboo on 2009-03-09
The only way your going to setup a system that is optimized for your processor, is to start with a kernel. The generic kernel Ubuntu uses works well on both my 500Mhz Celeron and my Intel Atom 230.

If you want an installation that is optimized for the i686 try somethng like [Arch Linux]("http://www.archlinux.org/download/").

Jim

---

### Post by Neo_The_User on 2009-03-09
I have my kernels built for my K7 processor, around 750K in size, 1000 Hz, Pre-emptiable whatever its called is set (super low latency) and RCU. super fast and small. Btw, I use arch linux all the time.

---

