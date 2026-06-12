---
title: "noobie needs help please - swap active but not really!!"
date: 2010-02-19
forum: Hardware
---

### Post by jahja on 2010-02-19
Hello all,

this is my first post. It should start with a big thanks in advance for any help - I can not believe how helpful and supportive the ubuntu community is!! I've learned a stupid amount here in the last few days...but not quite enough to fix this :( 

I'll try and keep to the point, but it is quite complex so appologies for rambling. I have searched and searched trying to fix this....

Basically, through combinations of messing around with Pysdm, gparted and disk utility, I have screwed a couple of things. I thought after a reinstall, it would all go back and not matter, but apparently this is not neccesarily so!!! 

So what I've been left with, my dilemma?? I have a fully functioning system which shows 2.8 gigs of swap space (which I now realise is too much....will deal with that later) but It can not use it. So the swap space is "active" in system monitor, but even when the RAM is fully cached, there is not a single byte running through the swap space lol.
It seems to be noted correctly in fstab, it shows up under "sudo swapon -s", it is there and recognized by the system, but it seems the system cannot use it. 

I know it is a healthy sign when the system doesn't need to use the swap, but before i Messed this up it would always have a few kilobytes running through it (which is effectively nothing, but enough to show its working!!), not the constant 0 bytes it shows now. The system is working fine, but not quite as smooth as it was....Even when I put swapiness value to 100, and open every application in menue, not a single byte runs through the swapspace. 

I've Included the results file from someone's boot up script from this site, since it contains lots of relative info. You may noticed I messed with a couple of things in fstab, but it is all still functioning exactly the same (so I changed the UUID label to /dev/x form, which shows exactly the same behaviour, and I changed the priority, which has not helped either) I do have a copy of the original, which doesn't change anything behaviour wise.

Thanks VERY much in advance for your help, I hope one of you smart people can help me - I am absolutely perplexed by this one lol!!

I'm not in any rush at least my system still works, but I'm sure some of you know how it is when you want it all running sweeeeet. 

Thanks again for any help,

Nick. 

Ps - results.text is that bootup-script result, some useful/relevant info in there...

---

### Post by Julita on 2010-02-19
Try activate swap partition in terminal
swapon /dev/sdb5

---

### Post by jahja on 2010-02-19
Hey there Julita thanks for response!

I wish it was so easy...

as stated, I can put swapoff and swapon again, and it registers as 'active' but really it is not....

Never a single byte being sent to it!

Thanks for the response though, keep them coming lol!!  :)

---

### Post by jahja on 2010-02-19
Polite bump....


sorry to bump so soon, this forum is busy haha!!!

Have been racking my brain for days on this one, so any opinions MUCH appreciated!!

---

### Post by jahja on 2010-02-19
OK ignore me please i'm a silly bugger.

It took about 24 hours of system uptime with 100 percent cached in RAM, but finally I have 800 kbs in my swap partition! yay.

---

