---
title: "Can't Resume on Battery Power"
date: 2008-11-07
forum: Hardware
---

### Post by greyfox1 on 2008-11-07
I know there have been may threads about hibernating/resuming but none seem to be the same situation as mine.  Bear with me if this is repeated elsewhere.

I have a problem with my girlfriend's IBM Thinkpad x40 laptop.  Hibernating/resuming works A-OK when I'm plugged in, but the laptop locks up while trying to resume while on battery power (I see the Ubuntu logo and "Waking Up, Please Wait" when the progress bar stops moving).  She is running Intrepid.  I don't believe this was a problem with Hardy but I can't say for sure.  I believe there may be useful information in various logs, but I'm not sure which logs or what to look for.  If anyone could get me started with finding useful diagnostic information, I would appreciate it.

---

### Post by greyfox1 on 2008-11-10
Bump

---

### Post by greyfox1 on 2008-11-12
Bump.  Anyone??

---

### Post by XiFu on 2008-12-31
Hello, greyfox1!

I have exactly the same problem with Intrepid on my ThinkPad X31.

First, I tried 
```
sudo pm-hibernate
```
in the console and hibernate worked everytime, even on battery.

But then, someone in the german Ubuntu forum gave me the tip to **add my user to the group "nvram"** and then it worked with the standard Ubuntu dialogue on battery too.

I hope it works for your girlfriend too,
greetings and a happy new year,
XiFu

---

### Post by greyfox1 on 2009-01-19
Hi XiFu, thanks for the tips.  I tried adding her to the nvram group but unfortunately, no change.  I'll try out the hibernate command and see if that changes anything.

---

