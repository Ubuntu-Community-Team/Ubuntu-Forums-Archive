---
title: "FOR THE LOVE OF GOD I BROKE MY SYSTEM! please help..."
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by simianMiscreant on 2005-05-11
Hoooooly crap I'm dumb. Okay, so PyMusique depends on libc6_2.3.2.ds1-21_i386.deb, and I thought it'd be clever to grab this off a webserver and force an install to get PyMusique working. OOPS! Apparently it isn't supported yet, and it's pretty much the most important package in the system - if I try and mark it for removal, it pretty marks 200 other packages for removal too. If I sudo dpkg -i a .deb of the older, supported one (libc6-i686_2.3.2.ds1-20ubuntu13_i386.deb), it doesn't work. PLEASE HELP I THINK I BROKE MY UBUNTU AGGGGGH!  :neutral:  :-x  ](*,)

---

### Post by jobezone on 2005-05-11
try and force install the older libc6 deb which works...maybe it will be all ok again!

---

### Post by simianMiscreant on 2005-05-11
doesn't work  ](*,)  ](*,) tried that PLEASE HELP AGGGH!

```
dpkg: regarding .../libc6-i686_2.3.2.ds1-20ubuntu13_i386.deb containing libc6-i686, pre-dependency problem:
 libc6-i686 pre-depends on libc6 (= 2.3.2.ds1-20ubuntu13)
  libc6 is installed, but is version 2.3.2.ds1-21.
dpkg: error processing Desktop/libc6-i686_2.3.2.ds1-20ubuntu13_i386.deb (--install):
 pre-dependency problem - not installing libc6-i686
Errors were encountered while processing:
 Desktop/libc6-i686_2.3.2.ds1-20ubuntu13_i386.deb
```

---

### Post by N'Jal on 2005-05-11
Can you not boot from the disc and replace the package?

There's always the old way, take note of what it removes then add them once libc6 has been fixed.

I did this once i think, creating a hybrid between Hoary and Warty, since my name's neil my mate called it Nelix (if you watch star trek you will get it) but i had to reinstall since i don't know enough on how to repair the damage. It was stuck as this hybrid system that couldn't install nor remove anything

---

### Post by simianMiscreant on 2005-05-11
actually fixed it - needed 386 version of the 686 one i had. thought problem was worse than it was. am huge noob. am forum idiot. am sorry.

---

### Post by az on 2005-05-11
Whenever a package requires you to upgrade to a not-yet-stable libc6, compile it from source with your current libc6.  You will need to add the source repositories (deb-src) for your app...

sudo apt-get build-dep <package>
sudo apt-get source -b <package>

---

### Post by N'Jal on 2005-05-11
simianMiscreant hey don't worry about it, i wouldn't have known about libc6 if i haddn't ball'sed it all up myself, i don't learn how computer's work i always seem to learn how they break, then learn how to make them work.

---

