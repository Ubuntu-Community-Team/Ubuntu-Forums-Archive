---
title: "Re-install applications"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-02-11
I may have to re-install Ubuntu per [this thread that no one feels like helping me](http://ubuntuforums.org/showthread.php?t=1066563).  How can I make a list of all the applications I have installed so when I re-install they will automatically download (or even keep what is already there)?

---

### Post by Mark Phelps on 2009-02-11
Take a look at AptonCD.

---

### Post by MaindotC on 2009-02-14
I just want a list of what is installed.  Isn't there a config file or something somewhere that describes this?

---

### Post by 2hot6ft2 on 2009-02-14
> **strAlan said:**
> I just want a list of what is installed.  Isn't there a config file or something somewhere that describes this?
Here you go.
> **handydan918 said:**
> Okay, this should be in the wiki, or something. It's so simple, yet so powerful.


```
sudo dpkg --get-selections
```


```
sudo dpkg --get-selections > softwarelist
```
At this point in the proceedings, you hose your system and reinstall, and then...

```
dpkg --set-selections < softwarelist
```


```
apt-get dselect-upgrade
```

Enjoy.
I looked at your thread and unfortunately I don't have any solutions to the problems you're experiencing. I hope this will help at least with the re-install and getting back to where you are and hopefully without the problems.

By the way that will create the softwarelist file in your Home folder.

---

