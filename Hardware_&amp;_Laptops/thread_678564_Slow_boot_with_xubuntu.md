---
title: "Slow boot with xubuntu"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by swaybox on 2008-01-26
Hi, I have a Pavilion ze2000 and I just installed xubuntu. When I boot my system it goes to a black screen for about 10 mins before going to the login screen. Im not sure what the problem is but if anyone knows what it possibly could be I would greatly appreciate it if you could help me out. Thanks!

---

### Post by rosegarden78 on 2008-01-26
Wowzers!  Could of been a bad installation disc.  Try burning a new one at 4x.  But why Xubuntu?  Ubuntu GG 7.10 comes with Compiz enabled and you can install Xfce yourself.  I have instructions [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981").  They both use the same kernel so there's no real difference except the session.

---

### Post by frankos44 on 2008-01-26
I had a slow boot problem on a laptop and it was due to screen resolution being set incorrectly in usplash.conf. In my case I could not see the splash screen but its worth a look all the same and set it occordingly. Error is due to Ubuntu not recognising the correct screen reselurtion during installation.

$ sudo nano /etc/usplash.conf
$ sudo update-initramfs -u

---

### Post by caterpillar322 on 2008-01-30
Thanks! This fixed a slow boot on a dell inspiron 5100 running xubuntu 7.10

---

