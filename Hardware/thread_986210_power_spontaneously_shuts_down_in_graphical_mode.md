---
title: "power spontaneously shuts down in graphical mode"
date: 2008-11-18
forum: Hardware
---

### Post by redpillstl on 2008-11-18
Hi, 

I have a dual boot laptop (a toshiba m35x-s149) running windows xp pro and ubuntu 8.04.1. When I boot in graphical mode it spontaneously shuts down at the 30 second mark after login.

Booting in recovery mode gets me to Text mode just fine. no spontaneous shutdown.

How do i diagnose what is happening?

thanks,
redpillstl

---

### Post by icanfly0307 on 2008-11-18
> **redpillstl said:**
> Hi, 

I have a dual boot laptop (a toshiba m35x-s149) running windows xp pro and ubuntu 8.04.1. When I boot in graphical mode it spontaneously shuts down at the 30 second mark after login.

Booting in recovery mode gets me to Text mode just fine. no spontaneous shutdown.

How do i diagnose what is happening?

thanks,
redpillstl

Hi, what do you mean by spontaneous shutdown? Does the entire computer power itself off without  warning? Do you have the same type of problems in XP?

---

### Post by redpillstl on 2008-11-18
> **icanfly0307 said:**
> Hi, what do you mean by spontaneous shutdown? Does the entire computer power itself off without  warning? Do you have the same type of problems in XP?

Does the entire computer power itself off without warning? yes
Do you have the same type of problems in XP? no
and it makes no difference on battery or AC power

thanks,
redpillstl

---

### Post by aurelieng on 2008-11-18
Overheating, maybe ?

Are you using binary drivers and/or desktop effects ? Are your fans clean and silent when you do nothing particular, or are they dirty and blowing at full speed when you enter the graphical mode ? Does the room temperature has an impact ?

---

### Post by redpillstl on 2008-11-18
> **aurelieng said:**
> Overheating, maybe ?

Are you using binary drivers and/or desktop effects ? Are your fans clean and silent when you do nothing particular, or are they dirty and blowing at full speed when you enter the graphical mode ? Does the room temperature has an impact ?

I don't think so. Fans are clean and silent.

I am pretty convinced it is a software issue.

how can i go back and look at the logs to get a clue?

thanks,
redpillstl

---

### Post by icanfly0307 on 2008-11-18
Try creating a new user account and logging into that. If your lappy doesn't shut down on you, it's your current user account that's the issue.

---

### Post by redpillstl on 2008-11-23
> **icanfly0307 said:**
> Try creating a new user account and logging into that. If your lappy doesn't shut down on you, it's your current user account that's the issue.

problem still present

redpillstl

---

### Post by icanfly0307 on 2008-11-23
> **redpillstl said:**
> problem still present

redpillstl

Hmmmmmm... Would backing up your files and reinstalling Ubuntu be an option? That would solve the issue.

---

### Post by redpillstl on 2008-11-30
> **icanfly0307 said:**
> Hmmmmmm... Would backing up your files and reinstalling Ubuntu be an option? That would solve the issue.

That was the first thing i tried.

thanks.

redpillstl

---

### Post by redpillstl on 2009-01-01
hi 

I did some reinstalls of earlier versions 

and determined the following:

7.04 works just fine
7.10 has same symptoms as 8.04 

I think it is time to file a bug report.

redpillstl

---

### Post by iSKUNK! on 2009-11-11
It's a buggy BIOS that's likely the problem. See [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242400) for details.

Upgrading the BIOS to Toshiba's latest should do the trick.

---

