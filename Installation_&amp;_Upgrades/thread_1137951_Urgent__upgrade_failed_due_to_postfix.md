---
title: "Urgent :: upgrade failed due to postfix"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by tech_cheetah on 2009-04-26
My ubuntu upgrade from 8.10 to 9.04 failed due to some issue in postfix. I have fixed the issue in postfix (by providing default values in main.cf file).
But then how do I make sure that the failed upgrade process restarts and complete properly ?
I have already tried running 
```
sudo apt-get upgrade
```
But my system is showing ubuntu 9.04 under System -> About Ubuntu
uname -a prints 2.6.27-11-generic

Please help !!
I am not sure if my system will boot when I restart it .

---

### Post by cariboo on 2009-04-26
In a terminal type:

```
sudo apt-get -f install
```

to finish installing missing dependencies and packages. then run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by tech_cheetah on 2009-04-26
Thanks God !!
My system started fine. I just had to reinstall NVidia drivers, and it is working fine :guitar:
In the new ubuntu I just noticed a few things new :
1. Notification style changed
2. Computer Janitor under Administration
3. New login/splash and gdm themes

I hope there are many other improvements undiscovered !!

---

### Post by tech_cheetah on 2009-04-26
Due to installation failure, cleaning operation was not performed.
How can I recover space from the downloaded packages for upgrade ?

---

