---
title: "Dual boot, want windows 1st"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by Daedalus123 on 2005-12-12
Hey all, I have an existing WinXp installation and now I'm installing Ubuntu, the installation asks me if I want to install GRUB to the master boot record, and that means that when I'm booting the computer Ubuntu will start automaticlly... I want Windows to start automaticlly when I start the computer. Any idea how to do it?

And I'm new to Linux so be "noobish" with the answers :D

---

### Post by NotJustANewbie on 2005-12-12
The answer to your question is simple...

[http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

---

### Post by bob phillips on 2005-12-12
amazingly simple - failed to find this on THREE googlings previously!

now i can safely load up linux on the wife's computer and not get beaten

thanks v much

---

### Post by NotJustANewbie on 2005-12-12
No problem ;)

---

### Post by Sp@z on 2005-12-12
I hope this is not a very old thread. The instructions from the link did not work for me. I installed Hoary from disk and upgraded to Breezy through the instructions about UPDATE found on these forums. IT has left 3 different OS on here (with RECOVERY) and as I count:

Other operating systems (8)
Windows 98,me (9)

I added the X_ sequence as directed but it still highlights the 510 kernal and boots to breezy. I want it to default to win98se

Thanx in advance..........

---

### Post by NotJustANewbie on 2005-12-12
[http://www.ubuntuforums.org/showthread.php?t=97558](http://www.ubuntuforums.org/showthread.php?t=97558)

You wouldn't encounter these problems if you didn't use M$ ;)

---

### Post by omair.majid on 2005-12-12
hmm...

is your x_sequence *really* correct? This caused me a lot of problems before...

Try this when setting x_sequence:
1) start counting from 0
2) count every title as an entry and increase x_sequence - even "other operating systems" is an entry

That's what worked for me. good luck!

PS: Just to clarify: x_sequence is not put there literally. you are supposed to put a number there for the entry you want to be automatically selected.

---

### Post by Sp@z on 2005-12-12
[QUOTE=NotJustANewbie][http://www.ubuntuforums.org/showthread.php?t=97558](http://www.ubuntuforums.org/showthread.php?t=97558)

You wouldn't encounter these problems if you didn't use M$ ;)[/QUOTE]

Thank you that helped. Also I just deleted the "Other" boot option and left the most current. And I apologize for my ignorance as I am 2 days into learning Linux Ubuntu, but what is M$? 

To omair.majid....thank you, I always start at 1 when counting. ST
arting at zero made the difference!

---

### Post by NotJustANewbie on 2005-12-12
You'll learn as you go along. Don't worry, must stick with it. I've been with Linux solidly for about one and a half years now still have troubles every day.

M$ is Micro$oft ;)

---

### Post by Sp@z on 2005-12-12
got ya thanx!

---

### Post by omair.majid on 2005-12-15
You should have seen how many problems *I* had when I started using linux ( and still have) this is like nothing..

gald i could be of help

---

