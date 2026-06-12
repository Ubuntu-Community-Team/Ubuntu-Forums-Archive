---
title: "installing dictionary in hardy via terminal"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2009-02-20
hi can any one give me the commands for installing wordweb dictionary in hardy system.

---

### Post by Partyboi2 on 2009-02-20
First you need to install wine
```
sudo apt-get install wine
```then download wordweb to your Desktop or where ever. Then change to where the downloaded wordweb file is eg.
```
cd ~/Desktop
``` then use wine to install the wordweb file you downloaded eg.
```
wine wordweb5.exe
```

---

### Post by abhinav.p on 2009-02-21
can i use wine to run a dictionary other than word web?the problem with word web is it doesnt prompt for a word.u have to enter all the letters before the word is defined.can u suggest a few dictionarys?

---

### Post by Partyboi2 on 2009-02-21
You only need to use wine when trying to installing windows programs. You could look at [[COLOR=Blue]kdict[/COLOR]]("http://www.zyxware.com/articles/2008/02/29/setting-up-wordweb-equivalent-dictionary-kdict-on-ubuntu") which works with ubuntu.

---

### Post by abhinav.p on 2009-02-21
thanks

---

