---
title: "How do i change settings from LIVE cd?"
date: 2008-08-27
forum: General Help
---

### Post by colobix on 2008-08-27
HI. i can't access internet on my ubuntu so I Have to use the live cd, I also do not have nautilus anymore on my ubuntu.
SO, how can I change settings from my live cd to my installed ubuntu?

PLease help.

---

### Post by Zill on 2008-08-27
I think you need to be more specific about what *is* working correctly and what *is not* working correctly.

Please specify *exactly* what errors your are seeing.

---

### Post by colobix on 2008-08-27
OK
I don't know. I tried that networking restart command but it wouldnt work
First of all, I need to repair my internet connection so I can install nautilus again.

---

### Post by colobix on 2008-08-27
I get an error with something like HALL and cant load desktop.

---

### Post by colobix on 2008-08-27
_____
bümp

---

### Post by mssever on 2008-08-27
Please post the exact error(s) you're getting.

---

### Post by colobix on 2008-08-27
OK the error message I get right after i've logged in is

INternal error
Faild to initialize HAL

Any idea on what this could be and how I can fix it?

---

### Post by colobix on 2008-08-27
______
bümp!

---

### Post by mssever on 2008-08-27
> **colobix said:**
> OK the error message I get right after i've logged in is

INternal error
Faild to initialize HAL

Any idea on what this could be and how I can fix it?
OK, try ```
sudo /etc/init.d/hal restart; echo $?
``` and post the result. If there are errors, look in /var/log/syslog  and /var/log/daemon.log for errors related to hal.

---

### Post by colobix on 2008-08-27
Isn't there any other solutions then all these commands?
I have to restart all the times now. i am using the same pc now as the installation with problems.
Any shorter commands I can remember in the head or faster way to fix this? And no, i will not reinstall the whole system again from scratch.

---

### Post by mssever on 2008-08-27
> **colobix said:**
> Isn't there any other solutions then all these commands?
I have to restart all the times now. i am using the same pc now as the installation with problems.
Any shorter commands I can remember in the head or faster way to fix this? And no, i will not reinstall the whole system again from scratch.
The problem is that there's no way to find out what your problem is without doing some troubleshooting. And we can't fix a problem if we don't know what it is.

The question is, is HAL crashing or not starting? If so, why? If not, how come other programs are complaining about HAL? I can't answer any of these questions based on the information you've provided so far.

---

### Post by colobix on 2008-08-27
I know but isn' there a way I can do these things in live cd mode were I are at the moment?

And none other programs are complaining about HAL as I know.
Nautilus is gone because I removed it by a mistake when I tried to fix up in things.
I also had to remove compiz because I got a white screen after login.

Ok so how can I fix this from my ubuntu CD?

---

### Post by colobix on 2008-08-27
bump

---

### Post by colobix on 2008-08-27
BüMp

---

### Post by mssever on 2008-08-27
> **colobix said:**
> bumpIt's considered bad etiquette to bump a thread more often than once per day.

> **colobix said:**
> I know but isn' there a way I can do these things in live cd mode were I are at the moment?

And none other programs are complaining about HAL as I know.
Nautilus is gone because I removed it by a mistake when I tried to fix up in things.
I also had to remove compiz because I got a white screen after login.

Ok so how can I fix this from my ubuntu CD?
Your live CD is a different install, so things will be different there. You can try mounting your partition(s) somewhere from the live cd, then doing ```
sudo chroot /path/to/your/partition
```and it might work, but the odds are against your being able to troubleshoot the problem from the live CD (aside from looking through the logs). Your live CD session will be controlling your hardware, not hte chroot environment.

In other words, more power to you if it works, but I'll be surprised if it does.

---

### Post by Zill on 2008-08-28
> **colobix said:**
> ...Nautilus is gone because I removed it by a mistake when I tried to fix up in things.
I also had to remove compiz because I got a white screen after login.
You seem to have seriously damaged your installation :-(

mssever has given you some good advice but if you cannot help find the problem then we cannot help you fix it!

My best advice is to reinstall.

---

