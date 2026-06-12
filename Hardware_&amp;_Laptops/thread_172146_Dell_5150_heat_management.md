---
title: "Dell 5150 heat management"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by capt_cope on 2006-05-08
Well guys I've installed ubuntu 5.10 on my old Dell 5150. This machine has had alot of troubles in the past, even in windows. I managed to fix most of them, however I fear that one of my internal temp sensors is on the fritz, which contributes to this beast overheating. In windows I circumvented that by installing a little gui that allowed me to control fan speeds in Windows. Now that I've run this laptop for more than just a few hours straight (writing a paper for criminal law :mad: ) the heat management troubles are coming back. Is there any simple (read this is the first linux disto I've EVER touched, let alone installed) way to set my fan speeds? All I want is to be able to run the cpu fan on high whenever the computer turns on. My little cooler/stand can't cut it if the cpu fan doesn't blow the hot air out from the case.
***EDIT***
Ok I found a linux port of my old gui, i8kfangui, but I don't understand how I install things like this. Maybe one of you can help? I downloaded a .tz file, I extracted it, but I don't know where to go from there.

---

### Post by slightly72 on 2006-05-08
i8kfangui should be downloadable from Synaptic (you have to set it up to access the universe and multiverse repositories -- there are some instructions in the Howto section of the site or the Ubuntu FAQ). You will also have to install gkrlm (hope the spelling is correct -- not near an ubuntu distribution now). There are a bunch of other tricks posted on this site to cool down Inspiron 51xx computers, should search for "inspiron", "5150", "5160" and/or "heat". I have an Inspiron 5160, with similar overheating problems, and managed to get this a bit under control (cleaning up the insides, disabling some services, taking the battery out for improved air flow), but this lines of laptops is known to have issues with the cooling system.

Another thing that you might need to do is to load the p4-clockmod kernel module (simply edit /etc/modules and add a line with just "p4-clockmod" on it). This shuld enable powernowd (the daemon that changes the processor clock rate based on the computer load) to correctly detect the speed steps in the P4, which might also help with heating -- though it does not do a lot for my laptop.

---

### Post by capt_cope on 2006-05-08
I've actually downloaded i8kfanutils, then gkrellm and i8krell. As of right now all i get in Gkrellm is a scrolling text where I have i8k placed. it reads: i8Krellm error: missing proc file, see (it restarts, but it's clear it was supposed to go on.) I have'nt played with linux long enough to know how to start trying to fix it. I've re-installed all files related to it but no dice.

---

### Post by slightly72 on 2006-05-08
hmm, not sure what's going on. You might also need to install lm_sensors to make it work, though I can't remember exactly. In any case, for the overheating problem I found that the other things (cleaning, p4-clockmod, disabling apmd) are more effective.

---

### Post by wylie348 on 2006-05-09
You have to force the module to load and also add it to /etc/modules.conf so that i8k loads on boot.  If you search the forums you WILL find it here - I keep refering to the posts when I do a re-install.
:P

---

### Post by infinitelink on 2007-05-02
a

---

### Post by infinitelink on 2007-05-02
This post, in expanded form, has been posted on a new thread at [http://ubuntuforums.org/showthread.php?p=2577082#post2577082]("http://ubuntuforums.org/showthread.php?p=2577082#post2577082"). Please see there.

> **capt_cope said:**
> I've actually downloaded i8kfanutils, then gkrellm and i8krell. As of right now all i get in Gkrellm is a scrolling text where I have i8k placed. it reads: i8Krellm error: missing proc file, see (it restarts, but it's clear it was supposed to go on.) I have'nt played with linux long enough to know how to start trying to fix it. I've re-installed all files related to it but no dice.

I'm in the same situation with an Inspiron XPS PIV running Feisty.

> **wylie348 said:**
> You have to force the module to load and also add it to /etc/modules.conf so that i8k loads on boot.  If you search the forums you WILL find it here - I keep refering to the posts when I do a re-install.
:P

How do you add it to modules.conf?

First, is the pathway to modules.conf just

sudo gedit /etc/modules.conf

or could it be elswhere?

Then, what pathway do we put into modules.conf with what other info?

Also, how do we "force it" (i8k...whatever) to start at boot with the rest of the kernel?

Please explain nicely, non-linux user (usually) here, only learning. Thanks.


Here's a discussion over on suseforums that might help anyone who might help us: [http://www.suseforums.net/lofiversion/index.php/t27436.html]("http://www.suseforums.net/lofiversion/index.php/t27436.html").

I learned from [http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k]("http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k") that "i8k.ko" ought to be in kernel/drivers/char, (my path is lib/modules/2.6.20-15-generic/kernel/drivers/char), but it's not: how does one put it there??? Also, where do I find i8k.ko and what do I do once I can see the thing? Unlike at [http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k]("http://ubuntuforums.org/showthread.php?t=216652&page=2&highlight=i8k") my problem isn't an old bios: I keep it up to date.

Thanks!

---

