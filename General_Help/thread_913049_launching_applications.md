---
title: "launching applications"
date: 2008-09-07
forum: General Help
---

### Post by iilux on 2008-09-07
Hello, I have a problem when I try to launch almost all of the applications I have on my OS. For example, if I try to launch Firefox, I have to wait 5-10 seconds for Firefox starting to load itself from hard disk. In this 5-10 seconds, on the panel an icon appears, on which it is written "starting Firefox".

It happens for all the applications, also for Terminal. For 5-10 seconds it appears on the panel "starting terminal", and then terminal appears and I can use it.

Can Somebody help me?

Thanks

---

### Post by schauerlich on 2008-09-07
This sounds like normal behavior. All applications will take a moment to start, especially if you haven't already opened them in that session. Is it taking an unreasonable amount of time, or is it just a little slow for your tastes?

---

### Post by wolfen69 on 2008-09-07
i guess it would also depend on your pc's specs.(RAM especially) an older computer will take longer to do anything. i have a fairly fast computer and it takes about 3 sec to open firefox.

---

### Post by Too Late on 2008-09-07
One possibility is that your /etc/hosts file has been messed up and therefore your applications can't find "localhost". I know, this sounds very strange, but it happened for me once, when the hosts file somehow broke itself (or actually it was a network-admin bug). If your DNS server is working, you won't even notice that, so that makes this theory even more unlikely. But when my DNS didn't work, the symptoms were identical to those you mentioned.

Probably the easiest way to check if this is the case is to look at your modem or NIC lights and see if they're blinking right after you've tried to launch an application.

edit: 5-10 sec for eg. terminal is definitely NOT normal, even on an old machine.

---

### Post by iilux on 2008-09-07
Thank you for your answering, I agree that 5-10 secondo for launching the terminal on a laptot with:
- 2.0 GHz clock, Centrino
- 1 GB RAM
- HD 5400 rpm

seems to be too much. 

Respect to Firefox, the question is that it takes about 6-7 seconds for being ready to use, but plus the 5-10 secondo in which I can read on the panel "starting Firefox"

So, what could I try to do?

Thanks

---

### Post by Too Late on 2008-09-07
> **iilux said:**
> So, what could I try to do?
So did you look at the activity lights of your network devices? There shouldn't be any activity during the "extra waiting time".

In addition, you could open System Monitor and see if there are any unusual things in the processes tab or in the cpu usage during the launching.

---

### Post by iilux on 2008-09-08
Hi, I did verify both the things you said, I did not notice anything strange. What else could I verify?

Thank you for your attention

---

### Post by iilux on 2008-09-08
Oh, excuse me, another detail: sometime, after the "extra time", the application does not start, and, on the panel, disappear "Starting application x".

---

### Post by iilux on 2008-09-11
Hello, I think i did discover the cause of my problem, that is: gksu. I did remove and reinstall it, and the situation, now, seems normal, also after many reboots. 

Now all the applications start without any "extra time".

The only little problem remaining is that when I start a root terminal, it appears on the panel, "starting terminal", and it does remain even after that the terminal is ready to be used. After a few second, "starting terminal" disappear from the panel, but the process gksu remains alive... It is not a great problem, because it gets about 1 MB, anyway if someone has the same problem, please tell me!

Thanks

---

