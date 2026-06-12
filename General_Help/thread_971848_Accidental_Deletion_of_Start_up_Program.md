---
title: "Accidental Deletion of Start up Program"
date: 2008-11-05
forum: General Help
---

### Post by DivineOmega on 2008-11-05
In System -> Preferences -> Sessions, I misclicked and have deleted one of the default start-up programs on my Ubuntu 8.10 install at work.

The program was top of the list and was something like 'actpi registry'. If someone running 8.10 could post this start-up entry's details I'd be most grateful.

Thanks!

---

### Post by tuxxy on 2008-11-05
**Name:** AT-SPI Registry Wrapper

**Command:** /usr/lib/gnome-session/helpers/at-spi-registryd-wrapper

---

### Post by DivineOmega on 2008-11-05
> **tuxxy said:**
> **Name:** AT-SPI Registry Wrapper

**Command:** /usr/lib/gnome-session/helpers/at-spi-registryd-wrapper

I was close! Thanks tuxxy.

---

### Post by tuxxy on 2008-11-05
heh you was indeed, no problem mate ):P

---

### Post by priegog on 2008-11-06
Wow this is a lifesaver, I just did this too, lol. 
Just out of curiosity, what does this do? I don't remember this entry from previous versions...

---

### Post by bp1509 on 2008-12-06
d

---

### Post by Topsider on 2009-01-25
"AT-SPI is Gnome's Accessibility Project" as quoted from [http://linux.softpedia.com/get/Programming/Libraries/at-spi-14849.shtml](http://linux.softpedia.com/get/Programming/Libraries/at-spi-14849.shtml)

In general, this new utility monitors user activity in certain programs and then provides useful information for the developers of the program.  Unfortunately, this sounds like a potentially dangerous program.  From what I've heard of this utility and others like it; though, the developers only expect for a small percentage of users to consciously enact the program to collect data (somewhere around 10%).

---

