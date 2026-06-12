---
title: "flash player"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by jojom271 on 2009-08-18
i tried installing adobe flash player 10 did the whole process when installing it said i had a older version it would not update. what do i do? i also tried using terminal it did not find it. maybe i am using wrong command name.

---

### Post by presence1960 on 2009-08-18
are you using 32 bit or 64 bit Ubuntu and exactly what did you try to do to install?

---

### Post by jojom271 on 2009-08-18
my comp is a 32bit/64 toshiba sat m305 s49052   i was trying to use meebo for im and i was having trouble using my internal cam it told me that i needed a flash player macro i think i followed link to adobe flash player for linux followed installation when installing it said i had older version and not complete install. i tried doing it through terminal it would not find it throught there also.

---

### Post by mhgsys on 2009-08-18
Remove the old flashplayer with 

```

sudo apt-get remove flashplugin-nonfree

```

and try to install flashplayer 10 again.

---

### Post by jojom271 on 2009-08-18
ojom271@jojom271-laptop:~$ sudo apt-get remove flashplugin-nonfree
[sudo] password for jojom271: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by presence1960 on 2009-08-18
are you using 32 bit or 64 bit ubuntu? I see your computer is 32bit/64bit capable, but which version of Ubuntu did you install 32 bit or 64 bit?

---

### Post by mhgsys on 2009-08-18
I could tell you this but since it's already here:
Have a look.
[http://ubuntuforums.org/archive/index.php/t-339828.html](http://ubuntuforums.org/archive/index.php/t-339828.html)

---

### Post by presence1960 on 2009-08-18
> **mhgsys said:**
> I could tell you this but since it's already here:
Have a look.
[http://ubuntuforums.org/archive/index.php/t-339828.html](http://ubuntuforums.org/archive/index.php/t-339828.html)

I would seem to think he used a deb file from Adobe's site not flashplugin-nonfree.

---

### Post by jojom271 on 2009-08-18
i told my terminal to remove adobe flash player with out using nonfree and it did it. then installed adobe flash player 10 thank you

---

### Post by mhgsys on 2009-08-18
@Presence1960 

I agree; 
Still it would work when he deletes flashplayer.xpt / libflashplayer.so
Don't you think?

Edit:
@Jojom271
 Good it's working. Keep up the good work.\

---

### Post by presence1960 on 2009-08-18
> **mhgsys said:**
> @Presence1960 

I agree; 
Still it would work when he deletes flashplayer.xpt and libflashplayer.so
Don't you think?

Edit:
@Jojom271
 Good it's working. Keep up the good work.\

yes, but the command with flashplugin-nonfree won't work because that isn't what was installed.

---

### Post by mhgsys on 2009-08-18
> **presence1960 said:**
> yes, but the command with flashplugin-nonfree won't work because that isn't what was installed.

Your right about that;
I saw that in the responds from TS, That's why I suggested to remove the files manually and linked him to the directions for that.

---

