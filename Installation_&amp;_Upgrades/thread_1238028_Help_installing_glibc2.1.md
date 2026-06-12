---
title: "Help installing glibc2.1"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by WesParmalee on 2009-08-12
Hey, I need help installing glibc2.1, I'm trying to install a game that is compatible with linux (Wolfenstein - enemy territory) and when I attempt to install, it fails, saying that it failed because glibc2.1 isn't installed, it offers a troubleshooting website, however it didn't help me solve the problem. Any help on getting glibc2.1 installed is greatly appreciated.

Here is a picture of the console:

[IMG]http://i31.tinypic.com/303flz6.jpg[/IMG]

---

### Post by mc4man on 2009-08-12
Somewhat similar and a bit of an answer about 'installing' glibcx.x (which you don't do) is here

[http://ubuntuforums.org/showthread.php?t=1237168](http://ubuntuforums.org/showthread.php?t=1237168)

In your case, if running hardy, intrepid or jaunty go in terminal

```
sudo apt-get install libgtk1.2
```

and take it from there

You may want to watch out going sudo -s too often, this would be good

```
 sudo ~/Desktop/et-linux-2.55.x86.run
```

---

### Post by WesParmalee on 2009-08-12
Thank you so much! :D It worked :)

---

