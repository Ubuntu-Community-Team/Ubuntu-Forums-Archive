---
title: "Ubuntu Laptop Help"
date: 2010-07-29
forum: Hardware
---

### Post by jasonodoom on 2010-07-29
My friend logged into her Ubuntu user but it logged her out and now she can't log in to her user or her Guest user. Please help!!!!!1 She's using a Lenevo Think Pad if that helps (an old version).

---

### Post by Goolie on 2010-07-29
> **jasonodoom said:**
> My friend logged into her Ubuntu user but it logged her out and now she can't log in to her user or her Guest user. Please help!!!!!1 She's using a Lenevo Think Pad if that helps (an old version).


Uhm, is there a graphical interface. . .what do you see on your screen?  

Where exactly are you stuck, lost password, blank screen?

A little more infos please!

---

### Post by jasonodoom on 2010-07-29
No blank screen. It's just that when my friend turns on her Laptop their is an automatic login in Ubuntu. After she's logged in, in 5 seconds she's logged out, This is the same for all users and now she cannot access her accounts without being logged out. If you can help I'll greatly appreciate it....

---

### Post by S.R on 2010-07-29
Does it seem to do a restart or does it shut down completely and she has to press the power button to start this system again?

---

### Post by jasonodoom on 2010-07-30
No, it just logs her out of her user and takes her to the log in screen.

---

### Post by S.R on 2010-07-30
OK try to fool in to not shutting down till a later time with ```
shutdown -h 45
``` This should give you 45 mins.

No dice there? Then maybe it is a runlevel problem try ```
init 1
``` or```
telinit 1
``` to see if single user makes a difference.

After that I think you are reduced to looking in the /etc.init.d for the scripts designed to control the processes.

Hope I was of some help. I hate to be the guy who reinvents the wheel.

---

### Post by jasonodoom on 2010-07-30
But I can't access the Terminal, it logs me off quickly before I get to it.....

---

### Post by S.R on 2010-07-30
Do you have a recovery mode option or an option to use an older kernel on startup? If not CTRL+ALT+F1 should work.

---

### Post by jasonodoom on 2010-07-31
I think so, thanks a lot I'll see if that works. If not I'll come back....

---

### Post by jasonodoom on 2010-08-02
> **S.R said:**
> Do you have a recovery mode option or an option to use an older kernel on startup? If not CTRL+ALT+F1 should work.
I tried  CTRL+ALT+F1  and it takes me to a Terminal like black screen. How do I access my user? And or fix the problem?

---

### Post by chrisinspace on 2010-08-02
> **jasonodoom said:**
> I tried  CTRL+ALT+F1  and it takes me to a Terminal like black screen. How do I access my user? And or fix the problem?

Log in using a known user name and password just like you would in the graphical interface.  Then try the terminal commands S.R gave you.

---

### Post by jasonodoom on 2010-08-02
Thanks!

---

### Post by jasonodoom on 2010-08-02
> **jasonodoom said:**
> I tried  CTRL+ALT+F1  and it takes me to a Terminal like black screen. How do I access my user? And or fix the problem?
After I logged in to the Terminal with my Admin account it says the user needs to be ROOT. And it still logs me off when I log in.

---

