---
title: "iPod Touch 1.1.5?"
date: 2008-08-16
forum: General Help
---

### Post by VivaLaEva on 2008-08-16
Awright, so I've been following the standard Ubuntu and iPod Touch thing, and so far I've jailbroken it, installed the BSD and SSH, mounted it...

Now my problem is this:

root@192.168.0.8's password:

The wiki entry has the root passwords up to 1.1.4, but I guess 'alpine' doesn't work with 1.1.5 'cause when I tried, it just re-entered the password prompt.

I couldn't find the password on google, either.

Any ideas on where I should go next?

Thank you!

---

### Post by VivaLaEva on 2008-08-16
Any ideas..?

---

### Post by VivaLaEva on 2008-08-16
'k, well, I tried downgrading to 1.1.4, and I STILL have the same problem.

How do I find out the root password?

---

### Post by VivaLaEva on 2008-08-16
I hate re-re-re bumping my thread, but I really do need help with this.
I'd prefer to not have to put my poor music collection through iTunes.

---

### Post by caseyann on 2008-12-11
Hey, Just found your post and thought I might offer some info. Sorry if you have already solved your problem.

On my system, I found that I had to enter the password twice to be able to ssh into my ipod touch, firmware 1.1.4

Maybe this will help you.

---

### Post by daqron on 2009-02-05
> **caseyann said:**
> On my system, I found that I had to enter the password twice to be able to ssh into my ipod touch, firmware 1.1.4

Yes, I had to do this as well (1.1.5). The password is still 'alpine' in this newer version so just type it twice when prompted and it should let you in. 

I'm sure everyone's following [these instructions]("https://help.ubuntu.com/community/PortableDevices/iPhone") which DO WORK for the iPod Touch v1.1.5 but you have to follow them very carefully. If you mess things up (like I did) it might help to rm -rf /media/ipod and then reinstall ipod-convenience in the Synaptic Package Manager.

P.S., following up on the idea of learning from my stupid mistakes, I offer this advice: don't change your root password on an iPod Touch; very bad things ensue. Very very bad.

---

