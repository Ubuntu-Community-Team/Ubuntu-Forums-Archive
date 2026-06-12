---
title: "Dell Inspiron 9300 problems"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by xRyanx on 2005-12-26
I was given a Dell Inspiron 9300 laptop as a gift, and I'm having problems getting Ubuntu installed on it.  I've tried with both Hoary and Breezy, and both have problems, so I know it's not an issue with the install disc.

Basically, it will work fine once the CD is booted, and I hit 'enter' to proceed with a default install.  Once it goes through all of that, and begins to actually install, the screen will flash on and off.  The install screen is only visible for a fraction of a second at a time, thus making it impossible to continue the install.  

I haven't been able to find anyone having this problem with Ubuntu or any other distros.  All of the articles that I have found have been people saying that they've had no problem with their Inspiron installs.  I just wanted to see if anyone has had similar problems, or knows what to do, before I deal with Dell's tech. support telling me that I'm SOL because they don't support Linux. 

Thanks in advance.

---

### Post by wanger123 on 2005-12-27
Hi, try typing this at the boot prompt: linux vga=771 pci=noacpi

please use search forums

see here from 2 days ago
[http://www.ubuntuforums.org/showthread.php?t=107682&highlight=vga%3D771](http://www.ubuntuforums.org/showthread.php?t=107682&highlight=vga%3D771)


[EDIT] more good sites
[http://www.rtr.ca/dell_i9300/](http://www.rtr.ca/dell_i9300/) and here [http://rtr.ca/dell_i9300/breezy.html](http://rtr.ca/dell_i9300/breezy.html)

cheers
wanger

---

### Post by Rinzwind on 2005-12-27
At the boot type:
```
linux vga=771
```

The pci=noacpi setting is not needed :)

Oh and I've got the same machine (ATI X300, 40 Gb, 512 Mb) and Ubuntu installed almost flawless: the multimedia keys didn't work out of the box, suspend and hibernate work unless you add the fxglr driver (and you need that for gaming :( )

---

### Post by wanger123 on 2005-12-27
Yeah, although I suggested the above advice, I didn't need any boot arguments to install Breezy onto my 9300 (80GB, X300, 1GB RAM etc etc). Just selected the default install, and all is good. :D 

wanger

---

### Post by xRyanx on 2005-12-27
Ah, thanks for the advice.  I have the install running right now.  I apologize for the re-post.  I had searched for it with a few different terms, but wasn't able to find it.

---

