---
title: "What causes the error :  already appears to be an X server running..."
date: 2004-12-20
forum: General Help
---

### Post by clparker on 2004-12-20
Hello, my name is charles, and while i am not a complete newb to Linux, I've been doing Ununtu for a month now and I have come to highly regard the work everybody does here. 
 
Any thoughts on what seems to be the key root cause of what's causing people to get "There already appears to be an X server running on display :0"???
 
From experience and reading it seems to happen after some people follow directions instructing them to use hoary repositories to get firefox 1.0 or some other upgrade. What is dear god's name is really causing all these people including myself to get "There already appears to be an X server running on display :0" some workarounds exist, but what is this? How can we avoid it for sure? What is causing it?

---

### Post by tavon on 2004-12-21
Hi,

I'm also experiencing this problem after upgrading firefox to 1.0 from hoary.  Quite strange indeed.

I'm currently killing X then starting X by typing `startx`.  Next time I boot, I'll probably disable gdm in my runlevel.  I can live with it for now but I'd like to know that this is something that will be fixed.  I've read other people not being able to revert back to firefox .9 and get the problem fixed and having to reinstall ubuntu.

Could someone please take a look into this?

---

### Post by clparker on 2005-01-24
FOLLOW UP, I FOUND A WAY TO PREVENT THIS!!!
 
 [http://www.ubuntuforums.org/showthread.php?t=11369]("http://www.ubuntuforums.org/showthread.php?t=11369")

---

