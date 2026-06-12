---
title: "kernel issue after upgrade (9.04-&gt; 9.10)"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by jennyjenny on 2009-10-20
Hello,

I did exactly what 23Meg says is a very bad idea. 
[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

I used the partial upgrade option on a working 9.10 system.

AMD64
Ubuntu 9.10

Now, when I run the system it is fine for about 3 minutes and then it goes into a hard freeze.  I am unable to get a terminal or move the mouse ... and the display clock stops changing the time.

What approach would you recommend I use to get my system working again?

xxoox 

-J-

---

### Post by jennyjenny on 2009-10-21
is using this command advisable for my situation?

$ sudo dpkg --configure -a && sudo apt-get -f install && sudo apt-get
--fix-missing install && sudo apt-get clean && sudo apt-get update &&
sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get
clean && sudo apt-get autoremove

xoxox,

-J-

---

### Post by garvinrick4 on 2009-10-21
> **jennyjenny said:**
> is using this command advisable for my situation?

$ sudo dpkg --configure -a && sudo apt-get -f install && sudo apt-get
--fix-missing install && sudo apt-get clean && sudo apt-get update &&
sudo apt-get upgrade && sudo apt-get dist-upgrade && sudo apt-get
clean && sudo apt-get autoremove

xoxox,

-J-

Just for the hell of it what time does your clock say in BIOS? Is it off time?

---

### Post by jennyjenny on 2009-11-19
Hi.. 

I checked the bios clock.  It looks fine.

Mea Culpa!   I am retreating to 9.04  ... 9.10 has been super problematic.

xx0oo0,

-J-

---

