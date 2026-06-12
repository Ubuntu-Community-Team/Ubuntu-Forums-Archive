---
title: "Freezing :["
date: 2008-07-21
forum: General Help
---

### Post by Mycah on 2008-07-21
I recently installed Ubuntu on my Gateway Laptop, and it worked fine. I loved the interface and how well it worked. But, now that I'm all situated, I have a serious problem that is annoying the heck out of me!

After a while of working, I began to notice that I cannot open any new programs. And I couldn't press the button to bring up the option to restart. So I have to hold in the power button to shut it off. This has happened several times. 

Also, my sound stops working, as in there is no sound coming from my speakers.

Also, programs that are open start locking up.

My system monitor show that the programs I try to open are running, just not open.

Why could this be happening?:mad:

Thanks in advance for your help!

---

### Post by Polygon on 2008-07-21
i used to be getting this as well. every time this happens, and you restart your computer, check the logs (applications> administration > system log

check teh kern.log and the messages log, and scroll to teh bottom, and then scroll up, so the numbers on the left side slowly go back down to [0.0000] and then they jump up again (which is where you restarted). 

are there any interestering messages there? I know i got a bunch of messages saying 'bug! cpu 0 stuck for 11 seconds! or something like that

---

### Post by lunarcloud on 2009-03-02
I'm having the same issue with jaunty. I get the first few seconds that the desktop is starting up in order to open programs, after that nothing opens, and the task manager says that they are open when they clearly are not.

This started happening to me after a reinstall, I'm thinking of removing all config files are reinstalling AGAIN. Maybe that'll help.

---

### Post by crokett on 2009-03-02
Mycah, I like your name.  That is my daughter's name although she spells it differently.

To help rule out any HW as the problem, boot the Ubuntu Live CD and use it for a while.  See if that also freezes.  If it does the problem is most likely hardware related.  If not, was there any particular package you installed before it quit working?  There might be some software with a memory leak.   
You can open your system monitor and watch the system memory to see if it all eventually gets used up.  If it does, there is some software running that is not freeing up memory.

---

### Post by lunarcloud on 2009-03-02
In the end, it turned out to be pidgin.

Pidgin autostarted after a little while and even plasma locked up.

There looks like a pidgin update is available, but I may switch to kopete (ewwww....) or something if it keeps it up.

---

