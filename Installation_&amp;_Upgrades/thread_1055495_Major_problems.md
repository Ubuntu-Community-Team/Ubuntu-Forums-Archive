---
title: "Major problems"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by firewarrior on 2009-01-30
Ok everyone I have a major problem with my ubuntu. I have Hardy 8.04 LTS. My problem started a few days ago when I had to reinstall Hardy. Now my problem is a couple of things. I am very new to the linux system. I've only been using it for about a month. 
My problems consist of the following
I have problems signing into the regular gnome and can only run ubuntu in the failsafe gnome or the failsafe terminal. I have read many different threads and can not find the solution to this problem. I have tried installing many of the different packages and to no avail. 
Second, this is dealing with my firefox browser. I can not seem to get the video or audio to play what so ever in the browser. I have tried installing the necessary files but still to no avail. Also with my browser sometimes when I click on a link it shuts my browser down and I have to restart it. 
Any help would be greatly appreciated.

---

### Post by taurus on 2009-01-30
The first one probably has to do with your graphic card and driver.  What kind of graphic does it have?

And for the second problem.  You just need to install the ubuntu-restricted-extras package.  You can install it from System -> Administration -> Synaptic Package Manager (or Applications -> Add/Remove) or from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by firewarrior on 2009-01-30
I have an on board graphics card. It is an ATI Readeon Xpress 200 and I'm also running a 64 bit if that helps. 
Thanks

---

### Post by firewarrior on 2009-01-30
Sorry for the second reply but I installed the second line of code and still no go on the playing of anything. Not on youtube or anywhere.

---

### Post by firewarrior on 2009-01-31
Thanks guys got the problem fixed. It was a problem with my vid.

---

