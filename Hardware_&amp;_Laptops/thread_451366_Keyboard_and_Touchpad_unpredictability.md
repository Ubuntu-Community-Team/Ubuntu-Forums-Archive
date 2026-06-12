---
title: "Keyboard and Touchpad unpredictability"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by Angafirith on 2007-05-22
I've been having some trouble with my laptop's keyboard and touchpad. It's a Compaq Presario v5210us. Sometimes, randomly, the keyboard would just start repeating what key I had pressed last. If I was in Thunderbird and had just deleted a single email, it would start deleting all of my email. If I was writing a document and hit space, sometimes it would just keep going. The same thing would happen with the Ctrl, Alt, and Shift keys, where Ubuntu (or the keyboard) would not recognize that I had let go of the key until I pressed it again. I also had problems with my touchpad, where it would stick in certain places and move unusually.

Eventually, I noticed that most of these problems disappeared when I was on my wired network, so I tried using ndiswrapper instead of bcm43xx for my BCM4318. Suddenly, the problem pretty much disappeared, only occasionally showing itself. I thought that the problem had been fixed. I noticed that at this point, the mouse generally only acted up after the computer had heated up a bit. I figured that perhaps the touchpad was heat based, causing problems when the machine got hot.

Unfortunately, this was not the case. I recently purchased a new Logitech Cordless Mini Optical Mouse (I can't seem to find the model number for this one anywhere). As soon as I plugged it in, the keyboard problem returned. The touchpad occasionally will now seem to have drastically reduced sensitivity, meaning that I pretty much have to use the mouse when I've plugged it in.

I figured that I'd post this here in case someone had some sort of solution for it: it's getting pretty annoying.

---

### Post by Angafirith on 2007-05-22
As this thread has made it to the 6th page with no responses, I believe a bump is in order.

---

### Post by groovomata on 2007-05-25
Did you check out this thread? I seem to be having a similar problem. Perhaps this will help.
[http://ubuntuforums.org/showthread.php?t=419675](http://ubuntuforums.org/showthread.php?t=419675)

---

### Post by febrile on 2007-05-26
And I've also got similar issues:
[http://ubuntuforums.org/showthread.php?t=450168](http://ubuntuforums.org/showthread.php?t=450168)

... but unlike @groovomata i don't think my touchpad problem's related to wireless (mine's plain ipw2200 and usually deactivated with hardware switch, but still get the problem).

---

### Post by Angafirith on 2007-05-31
I had removed the "bcm43xx" driver ages ago, and observed that the problem was resolved at the time. The issue is that it's back when I try to use my new Logitech Cordless Mini Optical Mouse (or whatever it's called). I was hoping that I could actually use the mouse without too many issues.

---

