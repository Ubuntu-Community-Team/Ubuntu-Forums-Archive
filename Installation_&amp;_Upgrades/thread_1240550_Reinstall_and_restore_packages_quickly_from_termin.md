---
title: "Reinstall and restore packages quickly from terminal?"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by sailthesea on 2009-08-14
I am ready to fully install Jaunty on my trusty Dell I am getting everything backed up, have my LiveCD burnt and am going to say goodbye to my Wubi install that has worked extremely well (Thankyou Wubigicians)
 I realised I've changed a lot of things over the last few months and don't fancy the hassle of reinstalling all the packages etc one at a time
In terminal could I generate a list of all the apt get and installation I've done so far and write it to backup cd? Then when finished installing I can simply open it up and bash them all back in without the whole add/remove synaptic saga?
Many Thanks if you can help a lazy person with a bad memory!:)

---

### Post by starcraft.man on 2009-08-14
See this [post]("http://ubuntuforums.org/showpost.php?p=7647357&postcount=3"), exactly what ya want.

To backup sources and keys also to save time, see my post [here]("http://ubuntuforums.org/showthread.php?t=1239775"). As well as earlier remarks.

I believe that answers your question. Be sure to restore the sources and keys (if you've installed any third party repos) and updating BEFORE trying to install all the packages as marked in first link. Enjoy.

---

### Post by sailthesea on 2009-08-14
Sweet! I knew I'd come  something across in the past Thanks a lot:)
Ah NO thats my final backup disc burning right now!

---

### Post by sailthesea on 2009-08-14
How do I save those to a USB stick then implement them after reinstalling? I won't be carrying a home partition over this will be a complete wipe and restore
 My terminal skills aren't quite at that standard yet:)

---

### Post by starcraft.man on 2009-08-14
> **sailthesea said:**
> How do I save those to a USB stick then implement them after reinstalling? I won't be carrying a home partition over this will be a complete wipe and restore
 My terminal skills aren't quite at that standard yet:)

The files are created wherever you direct them to. It follows standard path rules.

For example, in the mypackages file it is created in your current directory. To see the current directory type in a terminal:

```
pwd
```

To set a path outside that directory (the one said in pwd (print working directory btw) Use something like the following:
```
/home/username/Desktop/Backup/MyPackages
```
Path starts from root (first slash) and then continues until the mypackages file created in backup folder on desktop. 

For better understanding search google for absolute and relative pathnames. This is an absolute path because we start at root. Once you've the files created, simply drag em with Nautilus to whatever medium ya want like a USB or use the cp command (not necessary really). As a more advanced means, ya could in fact direct the files be created on the USB drive in question, use nautilus to find out the path to your usb drives and substitute it in. Also, see my terminal guide in sig for better explanation on pathnames as well.

---

### Post by sailthesea on 2009-08-14
:)Got it now Forgot to take root
 Will go at tomorrow had too much beer for sudo shenanigans 
 Thanks for the help

---

### Post by starcraft.man on 2009-08-14
> **sailthesea said:**
> :)Got it now Forgot to take root
 Will go at tomorrow had too much beer for sudo shenanigans 
 Thanks for the help

You should know by now, don't drink and sudo :).

---

### Post by sailthesea on 2009-08-14
> **starcraft.man said:**
> you should know by now, don't drink and sudo :).

+10000:)

---

