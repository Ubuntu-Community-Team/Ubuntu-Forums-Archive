---
title: "Slow unstable firefox"
date: 2008-11-03
forum: General Help
---

### Post by BetterSense on 2008-11-03
Firefox is being terrible ever since I upgraded to I.Ibex. 

It hangs/goes grey all the time. Or, I will enter text into an online form and it will freeze, so I press the key a few times, then it unfreezes and all the extra keystrokes instantly show up. Annoying stuff like this. Constantly I will be scrolling down with the arrow key, and it freezes, then unfreezez and scrolls all the way past where I wanted. Sometimes it just completely hangs and I have to kill and revive it. I have no idea why, if it's a plugin, or a bug, or what. I would use a different browser but I don't like konqueror, and kazahakase and midori crash constantly for me. So I would like to fix firefox back to being the awesomeness that it was, or failing that, i would like to find a nice replacement browser.

---

### Post by lordmyth on 2008-11-04
same problem i think... any solutions?

---

### Post by ShelJ on 2008-11-04
Bump.  For now I'm using Opera  ...  :(

---

### Post by capndeathstrike on 2008-11-04
Here's another BUMP.  I'm using Opera too and it's almost as slow as my broken Firefox.  Does anyone know how to fix this problem?

---

### Post by tsteele999 on 2008-11-05
Same issue here, too.

---

### Post by FlappySocks on 2008-11-05
See here
[http://ph.ubuntuforums.com/showthread.php?t=965579](http://ph.ubuntuforums.com/showthread.php?t=965579)

---

### Post by MockY on 2008-11-06
I have yet to experience a crash, but it is slow beyond anything and greys out every now and then, making surfing the Internet a painful experience. It really kicks my aggression nerve real hard. I have to go back to Hardy yet again. When on earth will I be able to install the latest Ubuntu without issues? *sigh*

---

### Post by FlappySocks on 2008-11-06
Its interesting how dependent we are on our favorite browsers.  Bugs in other apps are a nuisance, but our browsers....argghhhhh... I need my therapist. :)

---

### Post by JemW on 2008-11-06
+1. FF dreadfully slow... I have a clean 8.10 install...

---

### Post by FlappySocks on 2008-11-06
It's not just Firefox.  Opera crashes.  Epiphany (Gecko) crashes.  Epiphany (WebKit) is slow. Konqueror is slow.

Something common to browsers.  And not all web pages.

Java?

---

### Post by ShelJ on 2008-11-06
Check this out from the Release Notes ([http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)) and give it a try.  You may need openjdk-6.

```
Access to Java Runtime Environment

To use Java programs, you need to install the openjdk-6-jre package whch contains the Java Runtime Environment. If you want to develop Java programs, then install the openjdk-6-jdk package. To work with Java applets in the Firefox browser and compatible browsers on x86 architectures, you need to install the icedtea6-plugin package by hand. 

The JRE and the Java applet plugin are installed by default in the live session on the Ubuntu DVD, but are not currently installed elsewhere due to space constraints. However, a missing feature in the installer means that these packages will not be installed when installing using the graphical installer on the DVD, so you will need to install them afterwards.
```

Hope it helps.

---

