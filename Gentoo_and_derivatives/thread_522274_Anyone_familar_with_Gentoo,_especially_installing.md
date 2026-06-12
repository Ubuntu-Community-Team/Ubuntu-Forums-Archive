---
title: "Anyone familar with Gentoo, especially installing?"
date: 2007-08-10
forum: Gentoo and derivatives
---

### Post by happysmileman on 2007-08-10
I'd like to know is anyone there familiar with Gentoo, I'd like to install it on my external hard drive but not sure whether I'd be able to do it without damaging my current install of Kubuntu/Windows on my main drive...

My external drive is /dev/sda and my internal is /dev/hda...

Is it easy to install Gentoo onto an external drive? And how long should I expect install to take (approximately of course... 512MB RAM, 2.667Ghz, USB2.0).

Also what way should I go.... I was thinking of the LiveCD, but would it be better to get the LiveDVD instead, what does DVD have that CD doesn't?

---

### Post by igknighted on 2007-08-10
> **happysmileman said:**
> I'd like to know is anyone there familiar with Gentoo, I'd like to install it on my external hard drive but not sure whether I'd be able to do it without damaging my current install of Kubuntu/Windows on my main drive...

My external drive is /dev/sda and my internal is /dev/hda...

Is it easy to install Gentoo onto an external drive? And how long should I expect install to take (approximately of course... 512MB RAM, 2.667Ghz, USB2.0).

Also what way should I go.... I was thinking of the LiveCD, but would it be better to get the LiveDVD instead, what does DVD have that CD doesn't?

You really should have another PC available to have the handbook open while you install (or at least print the whole thing).  I know it is old school, but you really should install from the minimal CD.  Its tedious, you wont be able to use your computer for a day or two (unless you install WM like fluxbox to use in the meantime while big things like gnome/KDE compile).

Installing from stage3 (using the minimal CD) is where you will learn a lot.  It lets you see what you are doing easier and then when you have the system you will understand how to admin it better.  The handbook is great.  You might not have any idea what it is telling you at times, but follow it step by step and you will be fine.

Oh, the liveCD could get you up and running on a gentoo system in an hour (using pre-compiled binaries), but it is really buggy last I checked.  If this is fixed you could try it, but I think (at least the first time) you should use the minimal/stage3 install so you see what is going on behind the scenes.

---

### Post by happysmileman on 2007-08-10
Hmmm... i don't have another computer... And I don't mind using pre-compiled binaries at first, for the big stuff, I was planning to use pre-compiled stuff for big stuff like KDE anyway, though I'm thinking maybe I should compile them.

I might not do it for a while anyway so maybe in the future i'll have a day or two... But since I don't have another compuer or working printer LiveCD might be best way to go?

---

### Post by buntunub on 2007-08-10
There is only one way to do a proper Gentoo install, and thats by hand, compiling everything from stage3+. Any other method, and your not getting a completely optimized system.

---

### Post by happysmileman on 2007-08-10
> **buntunub said:**
> There is only one way to do a proper Gentoo install, and thats by hand, compiling everything from stage3+. Any other method, and your not getting a completely optimized system.

Yeah that sucks... Is it an installer where I follow instructions and it compiles based on what I answer.... Or is it like a shell where i compile everything myself?

---

### Post by igknighted on 2007-08-10
> **happysmileman said:**
> Yeah that sucks... Is it an installer where I follow instructions and it compiles based on what I answer.... Or is it like a shell where i compile everything myself?

Its a mix.  Compiling in Gentoo is nothing like compiling in Ubuntu.  Basically it is a package manager, but instead of downloading RPMs or DEBs, it downloads the source and an ebuild, which is essentially instructions on how to compile it and what dependencies it needs.  In short, instead of:
```
cd ~/pidgin-2.1
./configure --options
make
make install
```
it is simply:
```
emerge --options pidgin
```

So that part is easy, but the rest of the setup (config files, init scripts etc.) is hard.  Well, not hard, it just needs to be precise.  The manual walks you through it amazingly well, so you don't need to know it before hand, you just need to follow the directions.  You probably wont understand it all, I still don't and I've done almost 10 installs, but you pick up pieces that are useful, not just in Gentoo, but with all distros.

---

### Post by Bachstelze on 2007-08-10
> **igknighted said:**
> 
it is simply:
```
emerge --options pidgin
```


I beg your pardon but to set the configure options in Gentoo, you use the USE flags, you don't specify them on the emerge command.

> **buntunub said:**
> There is only one way to do a proper Gentoo install, and thats by hand, compiling everything from stage3+. Any other method, and your not getting a completely optimized system.

Huh ? So my system built from stage 1 is not optimized, then ?

Oh, and moved to the Gentoo subforum, too.

---

### Post by happysmileman on 2007-08-10
Ok then, another question... Can I do a stage3 install from something other than Minimal install CD... The minimal install CD seems to be "basic Linux with nothing else"... I only have a 512kbps connection so would prefer to not have to download stuff like KDE source... Is there a way to do a stage3 install on a CD with packages and stuff?

---

### Post by Bachstelze on 2007-08-10
> **happysmileman said:**
> Ok then, another question... Can I do a stage3 install from something other than Minimal install CD... The minimal install CD seems to be "basic Linux with nothing else"... I only have a 512kbps connection so would prefer to not have to download stuff like KDE source... Is there a way to do a stage3 install on a CD with packages and stuff?

You can do a stage 3 install from anywhere. Any Live CD you want, your already installed Linux, maybe even Windows... But let me ask you a question, if you want precompiled packages, why go with Gentoo ? Downloading the sources for something is no bigger than downloading a precompiled package, anyway.

---

### Post by seipherdj on 2007-08-10
Part of the gentoo experience is waiting for compile's, up to 48 hours for a complete system( ... like what ubuntu is after it is intalled..).My personal preference is Gentoo, its a great learning experience installing it.

If your looking for a quick install with allot of the learning aspect thrown in..... check out ArchLinux. You still do most things manually (alsa,x11,Desktop Enviorment......etc), but you are installing binaries ... which are super fast(always have the option of compiling though).

---

### Post by happysmileman on 2007-08-10
> **HymnToLife said:**
> You can do a stage 3 install from anywhere. Any Live CD you want, your already installed Linux, maybe even Windows... But let me ask you a question, if you want precompiled packages, why go with Gentoo ? Downloading the sources for something is no bigger than downloading a precompiled package, anyway.

I was thinking there may be a CD I could get with source packages already on it... i do want to compile, but I'd rather get all the downloading out of the way first

---

### Post by Bachstelze on 2007-08-10
Well, you can always download the source tarballs from another computer and copy them over but I don't know of any CD that has them. Versions move too quickly anyway, it would be outdated in no time.

---

### Post by igknighted on 2007-08-10
> **HymnToLife said:**
> I beg your pardon but to set the configure options in Gentoo, you use the USE flags, you don't specify them on the emerge command.

Sorry, the --options there were things like pretend, not use flags.  I should have been more specific.

---

### Post by happysmileman on 2007-08-10
Ah ok... i think i'll do that... And I don't mind downloading packages I suppose, I can always leave computer on overnight/while I'm at school if I need to.

Oh and one last question... The stage3+ install everyone is mentioning... Is that just following the Gentoo Handbook guide or is there something else I need to do... i can't really find any mention og the different stages in the handbook, except for the stage3 tarbell, so do i just get that from internet and compile anything from there on, or am I missing something?

Sorry if these are stupid questions

---

### Post by Bachstelze on 2007-08-10
The stage 3 tarball contains the base system plus a few other tools, including those required for compiling. So basically, all you do is :

=> Estract the stage 3 tarball to your Gentoo partitions.
=> Edit the config files to configure your Gentoo system and get ready for compiling.
=> chroot
=> Install whatever you want.
=> Reboot.

And you have your working Gentoo :)

---

### Post by happysmileman on 2007-08-10
Ah thanks, i'm ook now... And it doesn't look like it'd take that long (excluding KDE of course, which I'll build over night)... i built LFS in 12 hours

---

### Post by mips on 2007-08-10
> **happysmileman said:**
> Ah thanks, i'm ook now... And it doesn't look like it'd take that long (excluding KDE of course, which I'll build over night)... i built LFS in 12 hours

Word of advice, before compiling KDE I would recommend compiling something smaller like fluxbox, Firefox, Xchat etc. This way you can have a gui to browse with while doing stuff like KDE etc which could take a long time.

---

### Post by Bachstelze on 2007-08-10
> **mips said:**
> Word of advice, before compiling KDE I would recommend compiling something smaller like fluxbox, Firefox, Xchat etc. This way you can have a gui to browse with while doing stuff like KDE etc which could take a long time.

Why bother ? As I said, it is perfectly possible to do all the compiling from a Live CD.

---

### Post by mips on 2007-08-10
> **HymnToLife said:**
> Why bother ? As I said, it is perfectly possible to do all the compiling from a Live CD.

Very true, just my personal preference.

---

