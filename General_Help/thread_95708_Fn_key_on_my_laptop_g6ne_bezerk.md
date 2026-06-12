---
title: "Fn key on my laptop g6ne bezerk"
date: 2005-11-27
forum: General Help
---

### Post by mengqing on 2005-11-27
After i installed the ch5nese 5nput us5ng one of the howtos

n6w my Fn key has g6ne wr6ng.  i have to hold the Fn key inorder to type c6rrectly. 

this 6nly happens in GDM. when under tty1-6, it is fine

does anyone kn6ws h6w t6 fix it?? th5s 5s dr5veing me crazy:(

---

### Post by mengqing on 2005-11-27
how do I delete all the settings in X and install a new one??


and which module is the Fn key using so i can shut it down?? 

thx

---

### Post by Randy Sparks on 2005-11-27
sudo dpkg-reconfigure xserver-xorg will reconfigure Xorg, including the keyboard settings.

---

### Post by mengqing on 2005-11-27
[QUOTE=Randy Sparks]sudo dpkg-reconfigure xserver-xorg will reconfigure Xorg, including the keyboard settings.[/QUOTE]

i found out that by stopping anything under /etc/init.d/, the key would return to normal, but only for one session.. eg, if restart GDM, the key would not work again...


i tried reconfigure but it is same as stopping mapkey.sh

thx

---

### Post by persev on 2006-05-09
Found fix here
[http://ubuntuforums.org/showthread.php?p=999271#post999271](http://ubuntuforums.org/showthread.php?p=999271#post999271)

---

