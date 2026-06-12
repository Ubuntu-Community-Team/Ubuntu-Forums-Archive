---
title: "almost to wits end: xubuntu on old ibm laptop"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by stuart.reinke on 2009-04-25
Help please! I'm trying to install xubuntu 8.04 on an IBM thinkpad 380xd with a pentium processor and 32mb ram. according to the install cd It should work, but it doesn't. Every time I get past one obstacle another one pops up. 

first got message involving out of date acpi: used acpi=off and the installer started. 

selected keyboard, language, installer detected hardware, scanned cd-rom, then locks up while loading additional components.

I'm at a loss, what do i do now?

---

### Post by MadCow108 on 2009-04-25
I think 32mb ram is to little for xubuntu.
xubuntu is only lightweight compared to (k)ubuntu. my xubuntu jaunty still uses around 300mb ram. With minimal install you can get 8.04 down to maybe 50-100mb but probably not 32mb

I would consider other Distros like Puppylinux, Deli linux or damn small linux.

---

### Post by Sef on 2009-04-25
With that little ram, [Deli Linux]("http://www.delilinux.de/") would be the one to use.   That is too little for Xubuntu for sure and I believe also for puppy linux.

---

### Post by stuart.reinke on 2009-04-25
I tried deli linux. Now when i boot i get a GRUB error 15 from both the hard drive and the cd. xubuntu is the only cd that will start up for me. 

I hope you can help me. My 6 year old is counting on me to get "his" computer running so he can play his games.

---

### Post by Slim Odds on 2009-04-25
> **stuart.reinke said:**
> I hope you can help me. My 6 year old is counting on me to get "his" computer running so he can play his games.

"Kid pressure" or not, 32 MB is very small. Also, that hardware is very old so some of the support may not exist in a new release.

---

### Post by kerry_s on 2009-04-25
+1 it's way to old.

run down to toysrus and grab your kid a eee, there going for $200.
[http://www.toysrus.com/search/index.jsp?kwCatId=&kw=eee&origkw=eee&f=Taxonomy/TRUS/2254197&sr=1](http://www.toysrus.com/search/index.jsp?kwCatId=&kw=eee&origkw=eee&f=Taxonomy/TRUS/2254197&sr=1)

---

### Post by stuart.reinke on 2009-04-25
Thanks for the advice. I knew it was a long shot when I intercepted this machine on it's way to the dumpster. 

What about a command line only linux os? Is there such a thing? If so I wouldn't mind playing with it.

---

### Post by kerry_s on 2009-04-25
> **stuart.reinke said:**
> Thanks for the advice. I knew it was a long shot when I intercepted this machine on it's way to the dumpster. 

What about a command line only linux os? Is there such a thing? If so I wouldn't mind playing with it.

sure, but try straight debian base instead.
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

that's the net installer, it's now suppose to check how much ram and it will automatically use the lowmem option, so all you need to do is when it gets to package selection uncheck "desktop" & "standard" that will give you just a command line install.

---

