---
title: "HOWTO: Install software building it from source code using apt-build"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by psihodelia on 2009-01-04
*This HOWTO explains how you can significantly [COLOR="Red"]speedup[/COLOR] your Ubuntu system by recompiling slow software.*


**1. Introduction**

By default all Ubuntu software programs are compiled so, that they can run on even oldest processors like 486. This approach is commonly known as i386 architecture. Many other Linux distributives have their software compiled so, that it can run on Pentium Pro and newer processors only. It is known as i686 architecture and it is also becomes obsolete, because many of us nowadays (2009) have multi-core processors with more advanced internal command architecture. 

It means, that if you have newest processor and if you use Ubuntu software by default (targeted on i386 architecture), you do not use optimally your processor. Your software is slow!

This HOWTO will explain how you can recompile your software in order to set all architectural advantages your new processor provides in motion. [COLOR="Red"]You can speedup your Ubuntu system significantly![/COLOR]


**2. Install and configure apt-build**

Open terminal and install apt-build.
```
sudo apt-get install apt-build
```

Answer all questions like it is described below. Run following command, which will ask you about configuration options. Run this command each time you whant to change your build options:
```
sudo dpkg-reconfigure apt-build
```

Answer them properly:

> **Directory used by apt-build to download and build packages:**
_/var/cache/apt-build/build_

**Directory used to store packages built by apt-build:**
_/var/cache/apt-build/repository_

**Optimization level:**
_Strong_

**Add apt-build repository to sources.list?**
_Yes_

**Options to add to gcc:**
_-pipe_
This flag actually has no effect on the generated code, but it makes the compilation process faster. It tells the compiler to use pipes instead of temporary files during the different stages of compilation. 

**Options to add to make:**
Depending on how many cores your processor has:
_-jN_ (where N=NUM_OF_CORES_YOUR_PROCESSOR_HAS + 1)
For example, if you have Dual Core you set _-j3_. For a Quad Core you set _-j5_ and so on. This flag specifies  the  number  of jobs to run simultaneously (effectively utilizing different cores).

**Architecture:**
Select _prescott_ here if you have Intel Multi-Core or select _athlon_ if you have AMD processor. 


**3. Reinstall your software using apt-build**

Now, after you have set up apt-build, we are ready to reinstall our software, now it will be optimized for our hardware.

Let's try something simple enough like mplayer-nogui:
```
sudo apt-build --reinstall install mplayer-nogui
```

So, analogously you can install new software or reinstall software you already have. Most obvious candidates to be reinstalled are most often used applications:
totem, mplayer, audacious, evince, firefox, python, compiz-gnome, etc.

You can get a list of what software you have already installed by:
```
dpkg --get-selections | grep -v deinstall
```


**4. Rebuild your world**

Following command will recompile your whole Ubuntu system:
```
sudo apt-build world
```
Warning! It takes a lot of time depending on what processor you have. In fact, it could lead to less stable system and you better to do it with only lowest Optimization Level.


**5. Conclusion**

Hopefully, recipes from this HOWTO will help you to feel how really fast your Ubuntu can be.

**Good Luck and be fast!**

---

### Post by psihodelia on 2009-01-06
This approach of software installation is also preferable in comparison with Gentoo, where all software must be built from the source code, what takes a lot of time and each software upgrade in Gentoo can lead to a very unstable system. In Ubuntu, using an approach described above, user can flexible select optimization strategy, just rebuilding applications,  suspected in slow run-time.

---

### Post by InspiredIndividual on 2009-01-17
Interesting! I'm certainly going to try it with a couple of applications.

I do have a few questions though, just for my understanding. I can see it could be worthwhile to recompile your complete Ubuntu system. You invest a lot of time once to make your system run somewhat faster afterwards. However, what happens after your packages are updated? Do you need to recompile all packages every time they get updated? That means you need to invest time regularly, so you win less time on the whole, isn't it? Another question, how do you return to the original situation? Say, I've recompiled softwareA, and for some reason I want to return to the original situation with easy packages in Synaptic. Can I just reinstall softwareA using apt-get instead of apt-build?

---

### Post by psihodelia on 2009-02-11
> **InspiredIndividual said:**
> Interesting! I'm certainly going to try it with a couple of applications.

I do have a few questions though, just for my understanding. I can see it could be worthwhile to recompile your complete Ubuntu system. You invest a lot of time once to make your system run somewhat faster afterwards. However, what happens after your packages are updated? Do you need to recompile all packages every time they get updated? That means you need to invest time regularly, so you win less time on the whole, isn't it? Another question, how do you return to the original situation? Say, I've recompiled softwareA, and for some reason I want to return to the original situation with easy packages in Synaptic. Can I just reinstall softwareA using apt-get instead of apt-build?

of course you can deside either you should use aptitude or apt-build for install/upgrade any package. Normally, apt-build should be used to build only critical software (like media players).

---

### Post by digitalbenji on 2009-02-20
How will this work with updates?  Say I apt-built firefox this way, then an update for firefox is released.  Will the precompiled binary package get installed over my compiled one, or will it know to automatically recompile?  Or will it just not do any updates?

Thanks,

---

### Post by abcuser on 2009-03-15
Hi,
after executing step 3 command "sudo apt-build --reinstall install mplayer-nogui" on Ubuntu 8.10 I get the following error "**Missing source package name for source_by_source().**"

I searched the web and there was some bug in ubuntu jaunty 9.04, but I am using ubuntu intrepid ibex 8.10.

Any idea what is wrong?
Regards

---

### Post by walmartshopper67 on 2009-03-16
> **abcuser said:**
> Hi,
after executing step 3 command "sudo apt-build --reinstall install mplayer-nogui" on Ubuntu 8.10 I get the following error "**Missing source package name for source_by_source().**"

I searched the web and there was some bug in ubuntu jaunty 9.04, but I am using ubuntu intrepid ibex 8.10.

Any idea what is wrong?
Regards

Oh yeah - I have this problem too, and it's a HUGE pain when trying to rebuild world. The source packages are there, but it errors out with the cryptic message above. 

The bigger question might be is apt-build still being actively developed? As in should we/can we wait for aa new version at some point?

---

### Post by Vorlander on 2009-04-16
> **walmartshopper67 said:**
> Oh yeah - I have this problem too, and it's a HUGE pain when trying to rebuild world. The source packages are there, but it errors out with the cryptic message above. 

The bigger question might be is apt-build still being actively developed? As in should we/can we wait for aa new version at some point?


I have this same problem:
Missing source package name for source_by_source()

And if I try to apt-build world , then after several minutes it stops working with this kind of error

---

### Post by DracoMoye on 2009-08-05
> **Vorlander said:**
> I have this same problem:
Missing source package name for source_by_source()

And if I try to apt-build world , then after several minutes it stops working with this kind of error

You can remove package that don't have source from our /etc/apt/apt-build.list file for world build

---

### Post by Amurko on 2009-09-03
I'm thinking of using apt-build to build more optimal binaries of software that is most commonly run instead of doing "apt-build world" risking a less stable system.  Some obvious choices to apt-build are Firefox, Nautilus, Openoffice..  what are some commonly used libraries that suck a lot of CPU when being loaded and/or run that I can also consider doing apt-build on?

---

### Post by aktiwers on 2009-12-03
Does apt-build take care of config files?
And what is the difference between  prescott and nocona CFLAGS?

---

### Post by aktiwers on 2009-12-03
> **aktiwers said:**
> Does apt-build take care of config files?
And what is the difference between  prescott and nocona CFLAGS?

nocona is for 64bit and prescottt is for 32bit?

---

### Post by aftertaf on 2010-01-31
I'm building world right now on 64bit packages originally, on kubuntu 9.10 with the 4 cores compiling...

WIll tell you if more or less performance and stability :D

---

### Post by fher98 on 2011-01-01
Its been a while since I did this on gentoo and later on Debian... will give it a try with totem and someone stated above, maybe with firefox and other multimedia an ooffice

---

