---
title: "Sleep Errors"
date: 2008-07-22
forum: General Help
---

### Post by anotherdisciple on 2008-07-22
My Dell E1505 SEEMS to suspend just fine... it turns off the monitor, I can't hear any disks working, it makes my power light slowly flash on and off, etc. However.... 1 in 5 times (or less) that I turn it back on it gives me an error about failing to suspend.

Occasionally it won't let me use my keyboard when I turn it back on, but most of the time it works. So, it looks like it suspends, sounds like it suspends, smells... well... it looks and sounds like it suspends. What could be the issue? Is it just being a big stinkin' liar?

Some things I'm sure your are going to want to know:

1. All my specs are in my signature
2. I have Compiz, Emerald, and AWN turned on
3. I have tried making POST_VIDEO=. and POST_VIDEO=false as well as a few other suggested tweaks, but other ideas are welcome.
4. I am running Hardy (8.10)

Is there a way to print the error details? You know how if you run a program in the terminal it will print off any errors... and this is great for troubleshooting? Can I do that with Suspend/Hibernate?

Thanks in advance.

---

### Post by anotherdisciple on 2008-07-23
It's been over 24 hours... so I thought I'd better give this a bump before it gets lost in the mix!

---

### Post by anotherdisciple on 2008-07-24
Giving this the daily bump.

---

### Post by anotherdisciple on 2008-07-25
Day 4

---

### Post by anotherdisciple on 2008-07-26
Day 5

---

### Post by anotherdisciple on 2008-07-28
Day 6.... yes.... I'm persistent

---

### Post by rules on 2008-07-28
I recently had a problem where my laptop would not go sleep because it could not "stop" the wireless card (ndiswrapper) and as I'm not really using it at the moment, I uninstalled it and all was fine afterwards.

Might not be be what you need ... at least it will keep your post at the top :)

---

### Post by anotherdisciple on 2008-07-28
You know ... I've wondered about that. I heard something about blacklisting a wireless card... or something like that... is there a way I could test this out?

---

### Post by rules on 2008-07-28
The only way I can think of is just uninstalling your wireless card completely and see what happens.

When I was having the problem, it would show how it was shutting down services and it kept repeating wlan0. Strangly, now that I think of it, it no longer shows that window. Maby it stop the services quick enough not to bother now.

---

### Post by anotherdisciple on 2008-07-28
Well, I need my wireless to work... so that is a bummer option. I have an Intel PRO/Wireless 3945 that worked out of the box, so I don't know about uninstalling those drivers either... I just thought that it was automagically supported by the kernel... is this right? I sure didn't install a restricted driver for it.

---

### Post by anotherdisciple on 2008-07-29
Day 7

---

### Post by rudy.elgato on 2008-07-29
wish I had a fix for you.. 

don't mean to sound like Debbie Downer, but I've been looking, waiting for a fix for the suspend failing to resume problem I've had on my desktop for almost 2 months now...

---

### Post by anotherdisciple on 2008-07-31
whoops... missed a day... so....

Day 9

---

### Post by anotherdisciple on 2008-08-05
Day 13... woo hoo!... I'm setting a record for longest unanswered post... haha

I'm hoping that people will just get sick of hearing from me and give me some things to try.

---

### Post by Paradoxalley on 2008-08-05
> **anotherdisciple said:**
> Day 13... woo hoo!... I'm setting a record for longest unanswered post... haha

I'm hoping that people will just get sick of hearing from me and give me some things to try.

the best place to start for any kind of debugging related to sleep, etc. is with a utility called "dmesg"

open a terminal and type:
```
dmesg
```
then post the optput and we can get started working on your sleeplessness ;-)

---

