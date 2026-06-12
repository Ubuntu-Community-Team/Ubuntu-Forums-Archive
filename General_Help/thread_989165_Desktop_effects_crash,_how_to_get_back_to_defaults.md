---
title: "Desktop effects crash, how to get back to defaults?"
date: 2008-11-21
forum: General Help
---

### Post by kdfox on 2008-11-21
I am a new linux user, so bear with me.  i am using kubuntu/intrepid.  when i enabled the desktop effects my screen went white, then black, but u still have the mouse.  when i logout or restart and log back in i get the same thing.  i am not as concerned as to why it's happening as i am with how to rest to the defaults if i can't see the desktop. my instinct is to use the live cd to go into the file system and alter a setting somewhere but i have no idea what file to alter or how to alter it.

help!

thanks in advance
kdf

---

### Post by Marius Derekus on 2008-11-21
It sounds like you have a intel 845 chipset. here is how you can boot up. Boot in recovery mode, select run as root. Type this in the terminal.

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

Then select resume normal boot. If you would like to have it installed later just in case, just type

```
sudo apt-get install compiz
``` but don't enable it or the problem will come back.

Me and a few others are on another thread trying to make desktop effects work on that chipset (this is a known bug), if you would like to help, here is the link [http://ubuntuforums.org/showthread.php?p=6220182](http://ubuntuforums.org/showthread.php?p=6220182)

If you didn't understand my instruction's or they didn't work, just ask, i'll try my best to help.

---

### Post by error919 on 2009-03-01
I am having a similar problem.
Except instead of having an intel chip 
we have amd sempron. Although I tried what
was said and nothing happened.
If it would help I will try it again and  post
what it had said.

---

### Post by error919 on 2009-03-01
bump

---

### Post by error919 on 2009-03-01
bump 2 need help

---

### Post by error919 on 2009-03-01
ok well when i try
sudo apt-get remove compiz
it says something like
cannot remove compiz because compiz is not installed

---

### Post by error919 on 2009-03-01
anyone help please????

---

