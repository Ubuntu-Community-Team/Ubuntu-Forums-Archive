---
title: "monitor &amp; display module error"
date: 2008-07-10
forum: General Help
---

### Post by lafferjm on 2008-07-10
I installed kubuntu yesterday and i am having trouble changing my resolution.  I open system settings and click on monitors & dispaly and get the following message:

The module Monitor & Dipslay could not be loaded

```
The diagnostics is:

possible reasons:

     -An error occurred during your last KDE upgrade leaving an orphaned control module

     -You have old third part modules lying around
```


How exactly would i fix this problem?

---

### Post by f37u5g0d on 2008-07-10
sudo dpkg reconfigure -a in a terminal should solve your problem.

---

### Post by lafferjm on 2008-07-10
I did that and i still get the same error.

---

### Post by f37u5g0d on 2008-07-10
I'm sorry slight typo.  I meant to type sudo dpkg -configure -a

---

### Post by lafferjm on 2008-07-10
I figured there was some kind of typo so i had ran ```
sudo dpkg-reconfigure -a
```  and was still getting the error.  Then i just tried to run what you just posted and it said that it wasn't a parameter.  Then i tried typing it together and it said command not found.

---

### Post by ChompTheMan on 2008-07-10
Do you have *kde-guidance* installed?

---

### Post by lafferjm on 2008-07-11
yes.  And also if it helps it says to fix the problem i have to delete the packages that are just lying around, but i don't know which ones to delete.

---

