---
title: "problems with radeon x1300 mobility on laptop"
date: 2008-07-01
forum: Hardware
---

### Post by jdmneon on 2008-07-01
hey I'm relatively new to Ubuntu, I wouldn't consider myself an advanced user but i'm not a total noob either, I want to make Ubuntu my main operating system but I can't for the life of me get it to recognize my graphics card

I used Envy-Ng and it said it detected it, it then installed the packages but I restart and I still don't see any color bars. I go to the hardware drivers and it says ATI accelerated graphics driver is in use. I'm not good at compiling source code but if thats the only way then I guess i'll have too.

before you ask I read the other threads about this graphics card and tried the suggestions but it didn't help as already stated the graphics card is the ati-mobility x1300, I really need some help thanks in advance.

---

### Post by stchman on 2008-07-01
> **jdmneon said:**
> hey I'm relatively new to Ubuntu, I wouldn't consider myself an advanced user but i'm not a total noob either, I want to make Ubuntu my main operating system but I can't for the life of me get it to recognize my graphics card

I used Envy-Ng and it said it detected it, it then installed the packages but I restart and I still don't see any color bars. I go to the hardware drivers and it says ATI accelerated graphics driver is in use. I'm not good at compiling source code but if thats the only way then I guess i'll have too.

before you ask I read the other threads about this graphics card and tried the suggestions but it didn't help as already stated the graphics card is the ati-mobility x1300, I really need some help thanks in advance.

The following package should get that card working:

```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by jdmneon on 2008-07-09
it says xorg-driver-fglrx is the newest version, but I still don't see any color bars or static when I run the test and I am unable to play any games, I could play games (although at around 5 fps) before I installed the ati graphics driver but now they won't even start, any suggestions?

---

