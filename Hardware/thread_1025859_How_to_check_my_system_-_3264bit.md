---
title: "How to check my system - 32/64bit?"
date: 2008-12-30
forum: Hardware
---

### Post by OinkOink2 on 2008-12-30
This isn't a dumb question.

My CPU is AMD Turion x64 TL-50, but I dunno if my system is 32bit.
I want to install Deluge but have conky show the stats. With reference to this post: [http://ubuntuforums.org/showthread.php?t=946664]("http://ubuntuforums.org/showthread.php?t=946664"), this can only be achieved by downloading the package on their website.

The packages on their website are for 32 and 64bit systems. I was wondering how I would check if my system will be capable of 64bit?

...I should have found this out before actually installing Ubuntu! Alas I didn't and went for the default 32bit install.

---

### Post by markp1989 on 2008-12-30
type 

```
 uname -a 
``` in to the terminal

and the output will say

x86_64 for 64bit

i386 for 32bit

---

### Post by OinkOink2 on 2008-12-30
Cheers

---

### Post by tornadof3 on 2008-12-31
Although it looks like you have a 32bit install (and hence need 32 bit packages) for your current set up, I can say that if at some point in the future when you upgrade, the x86_64 version should work fine with that processor, and you will notice it is a little faster. Also, unlike with other linux distros, ubuntu 64 seems to just "work" and doesn't break with things like java applets, flash or other multimedia software.

---

### Post by Ahadiel on 2008-12-31
[quote="tornadof3"]Also, unlike with other linux distros, ubuntu 64 seems to just "work" and doesn't break with things like java applets, flash or other multimedia software.[/code]

That's most likely because they haven't upgraded to flash64 and java64 yet.

---

### Post by igknighted on 2008-12-31
> **"tornadof3"]Also, unlike with other linux distros, ubuntu 64 seems to just "work" and doesn't break with things like java applets, flash or other multimedia software.[/quote]

[QUOTE=Ahadiel said:**
> That's most likely because they haven't upgraded to flash64 and java64 yet.

No distro's have... flash's 64bit plugin and java's 64bit plugin are still in development releases.  The reason Ubuntu's "just works" is because it automatically configures 32bit plugins to work via ndiswrapper.  However, even in development state, flash's 64bit plugin is much better than the "stable" 32bit one with ndiswrapper, so in order to truly get a usable 64bit system, you need to manually install it anyways.

I have not used java's 64bit plugin, so I cannot say either way if the 64bit alpha is better than 32bit w/ ndiswrapper

EDIT: Sorry, ndiswrapper should say "nspluginwrapper".  ndiswrapper is for wifi cards.

---

