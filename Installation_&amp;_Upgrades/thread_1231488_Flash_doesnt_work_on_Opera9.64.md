---
title: "Flash doesnt work on Opera/9.64"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by -=hazard=- on 2009-08-04
I just installed Opera 9.64 and seams flash doesn't work. I tried with flashplugin-nonfree, then with flashplugin-installer, installing from terminal or just copying the .so file on opera plugin folder. I have uninstalled all other flash stuff that comes with ubuntu so there is no conflict. Firefox works with all the methods but opera don't. Anyone know a solution?

---

### Post by running_rabbit07 on 2009-08-04
Go to myspace.com the front page should offer up a new flash driver if it is not working.

---

### Post by -=hazard=- on 2009-08-04
> **running_rabbit07 said:**
> Go to myspace.com the front page should offer up a new flash driver if it is not working.

I'm there but nothing happens and if I go to videos the screen just stay blank like on youtube.

---

### Post by voy on 2009-08-11
Same problem here. Nobody knows a solution for this?

---

### Post by Lampi on 2009-08-11
it works here ... so what does **about: plugins** tell you? Anything pointing to libflashplayer.so? And what update-alternatives for flash have you got? Here is what I got:

```
~$ ls -la /etc/alternatives/ | grep flash
lrwxrwxrwx   1 root root    44 2009-07-31 16:04 firefox-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so
lrwxrwxrwx   1 root root    44 2009-07-31 16:04 iceape-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so
lrwxrwxrwx   1 root root    44 2009-07-31 16:04 iceweasel-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so
lrwxrwxrwx   1 root root    44 2009-07-31 16:04 midbrowser-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so
lrwxrwxrwx   1 root root    44 2009-07-31 16:04 mozilla-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so
lrwxrwxrwx   1 root root    44 2009-07-31 16:04 xulrunner-addons-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so
lrwxrwxrwx   1 root root    44 2009-07-31 16:04 xulrunner-flashplugin -> /usr/lib/adobe-flashplugin/libflashplayer.so
```
mozilla-flashplugin is the one opera uses, or you can move the libflashplayer.so binary to /usr/lib/opera/plugins right away. Also make sure you have no conflicting flash plugins installed (swfdec, gnash)

---

### Post by ralphwiggum on 2009-08-12
I got it to work following [http://ubuntuforums.org/showthread.php?t=1228708]("http://ubuntuforums.org/showthread.php?t=1228708")

---

### Post by SirWeazel on 2009-08-12
I've spent alot of time also trying to get flash to work correctly with 9.64.  I ended up installing opera 10 beta 2, and have been completely happy with it. I think it is a little more responsive then 9.64. It also hasn't had any problems with flash or java with it, and have been happy with it.  I haven't encountered any problems either, that usually come with a beta release.

---

