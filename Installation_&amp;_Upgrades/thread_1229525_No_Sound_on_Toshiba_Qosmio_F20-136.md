---
title: "No Sound on Toshiba Qosmio F20-136"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by ak45 on 2009-08-02
Hi

Im new to linux so please can someone help me as I have had this problem on all a few differnt disto's including Mint. I have a Toshiba Qosmio F20-136 and have installed Ubuntu but cant get the sound working on it. Unfortunately the linux drivers are not available on the Toshiba support website for th Qosmio.

When I check what driver is being used it says "Analog Devices AD1981" as far as I know this is supposed to be correct but may be wrong. Would appreciate if anyone could help me out with this

AK

---

### Post by P4man on 2009-08-12
tell us what version of ubuntu you're running. Also provide output of ```
lspci
```.

Something to check quickly is opening a terminal and type:

```
alsamixer -c 0
```

there use the arrow keys to move the mixer sliders, make sure nothing is muted that shouldn't be muted (notably PCM).

As to your rant post about not getting replies.. please understand there thousands of posts created here each day. Everyone helping out is doing so on a voluntary basis. There are simply many more new users with questions and problems then there are people able to assist. Therefore, its a good idea to search this site, use google and try finding a solution yourself. When you can't find it, then post, but tell us what you already tried. There are a gazillion "i have no sound" threads out there that may (or may not) help you.

---

### Post by P4man on 2009-08-12
this may help too:

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301)

---

