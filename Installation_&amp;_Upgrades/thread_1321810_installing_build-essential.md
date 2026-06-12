---
title: "installing build-essential"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by itachis.eyes on 2009-11-10
ok i seem to have a bit of a paradox here. i ran a check and found that i don't have build-essential. and on the particular machine i'm working with, there isn't an internet connection, so how am i to compile the source code of build-essential without build-essential?

just to make sure i'm not reading the out put wrong i checked with:

```
sudo aptitude install build-essential
```and the out put i got was:

```
reading package lists...done
building dependency tree...done
reading state information...done
initializing package states...done
couldn't find any package whose name or description matched "build-essential"
couldn't find any package whose name or description matched "build-essential"
0 packages upgraded, 0 newly installed, 0 to remove, and 0 not upgraded
```

---

### Post by tchoklat on 2009-11-10
[http://ubuntuforums.org/archive/index.php/t-381532.html](http://ubuntuforums.org/archive/index.php/t-381532.html)
 
I actually thought it was installed automatically, (can't check as I am on a windoze machine at the moment). Check in synaptic!

---

### Post by itachis.eyes on 2009-11-10
> **tchoklat said:**
> [http://ubuntuforums.org/archive/index.php/t-381532.html](http://ubuntuforums.org/archive/index.php/t-381532.html)
 
I actually thought it was installed automatically, (can't check as I am on a windoze machine at the moment). Check in synaptic!

PERFECT! i'm up and running. thank you so much

---

### Post by Tottish on 2010-03-27
**[COLOR="Red"]SORRY FOR THE DOUBLE POST!!! PLEASE DO NOT ANSWER THIS POST BU GO TO [This Thread]("http://ubuntuforums.org/showthread.php?p=9035543#post9035543") INSTEAD!!![/COLOR]**

Hi! (I'm new here and very much a Linux noob)
So that solves it if you have a CD drive... :p

What to do if a poor fella (like me) was to have a system with no CD drive?

I installed from USB PENDRIVE and I suppose there have to be some command corresponding to apt-cdrom but for the USB drive but I can't find one.

Help, please. =)

Have a nice day!
/Tottish

---

