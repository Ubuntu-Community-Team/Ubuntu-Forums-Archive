---
title: "Firefox Audio Problem"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by cgdoc7 on 2006-05-21
I'm am new so please be gentle......I have recently converted from XP and have managed to set most everything up, starting with 5.10.  I am now using Dapper but for some reason when I get on firefox there is no sound with any site I visit (i.e. myspace, youtube, napster, foxnews).  I still have sound on my comp (i.e. I play a dvd or something) so I assume the issue lies with firefox.  Any ideas?

---

### Post by louis_nichols on 2006-05-21
The problem is with flashplayer, which directs sound throguh oss, which, in turn, doesn't support mixing.

An easy way around this (the one I use - you can find others on the forums, if you run a search) is to always start firefox with the command

aoss firefox

I usually update the launchers for this, too.

---

### Post by shuttleworthwannabe on 2006-05-21
Thanks It works great: I also installed alsa-oss from repo and changed the sound to use ALSA under preferences>multimedia systems selector

---

### Post by cgdoc7 on 2006-05-21
Thanks Louis!  Worked perfectly!

---

### Post by louis_nichols on 2006-05-21
wellcome! :) enjoy!

---

### Post by panurge77 on 2006-05-24
How could I apply that using firefox 32 bits on amd64 without chroot?

---

### Post by louis_nichols on 2006-05-25
[QUOTE=panurge77]How could I apply that using firefox 32 bits on amd64 without chroot?[/QUOTE]
Sorry, but I can't help there. My knowledge about 64 bits and their issues is very limited.

---

