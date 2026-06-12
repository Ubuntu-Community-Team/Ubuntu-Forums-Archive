---
title: "Upgrade Freezing"
date: 2008-08-09
forum: General Help
---

### Post by AdNZL on 2008-08-09
Hi, I'm not sure if this is normal, and I'm gonna leave my computer running over night to see if it unfreezes. But basically it's gotten most of the way through the upgrade, and most of the way through the "installing upgrades" part but has frozen at the configuring locals part.

What are my options at this point? I know your not sopposed to restart the computer, but if its not going to continue with the upgrade I have no choice. Will it be able to repair the damage done from a hard reset at this point?

---

### Post by AdNZL on 2008-08-09
Well after waiting about 8 hours for the up date to wake up I finally lost what little patience I had left and restarted the comp. Not surprisingly ubuntu wouldn't restart in normal mode, so I started in recovery mode and went to the repair packages option. Interestingly enough the package repair has gotten stuck in exactly the same spot as the upgrade.


[B]*the last few lines of output look like this...*

Setting up libavahi-ui0 (0.6.22-ubuntu4) ...

Setting up libmms0 (0.3-6) ...

Setting up locales (2.7.9-4) ...
generating locals...
  en_AU.UTF-8....
[/B]


And thats as far as it gets :( I'm thinking I'll just need to reinstall, but it'd be nice if I could fix it.

---

### Post by cdtech on 2008-08-09
Try running "sudo apt-get autoremove && sudo apt-get clean". Then do the "sudo apt-get update" If you get errors during the update run "sudo dpkg --configure -a". Then try your upgrade.

---

### Post by AdNZL on 2008-08-09
> **cdtech said:**
> Try running "sudo apt-get autoremove && sudo apt-get clean". Then do the "sudo apt-get update" If you get errors during the update run "sudo dpkg --configure -a". Then try your upgrade.

Ok I tried what you told me, and the problem I get is that when I enter, **sudo apt-get autoremove && sudo apt-get clean**, I get the message **dpkg was interupted, you must manually 'run dpkg --configure -a' to correct the problem.** which after a short amount of time leads me back to the same point the computer was getting stuck at, and remains stuck. :(

---

### Post by cdtech on 2008-08-09
> **AdNZL said:**
> you must manually 'run dpkg --configure -a' to correct the problem.[/B]

And you did manually run this command?

---

### Post by Crafty Kisses on 2008-08-09
> **AdNZL said:**
> Ok I tried what you told me, and the problem I get is that when I enter, **sudo apt-get autoremove && sudo apt-get clean**, I get the message **dpkg was interupted, you must manually 'run dpkg --configure -a' to correct the problem.** which after a short amount of time leads me back to the same point the computer was getting stuck at, and remains stuck. :(

Yeah, you're going to have to run that command stated above, and then you can run the following ones, it looks like one of your packages got interrupted, no big deal.

---

### Post by AdNZL on 2008-08-10
yup I did it manually. The first commands don't work as it comes up with the error message,

 **dpkg was interrupted, you must manually 'run dpkg --configure -a' to correct the problem.**

so I typed in 

**dpkg --configure -a**

which gets me back to the point where I get stuck.

yes the update was interrupted, I interrupted it when it did nothing for eight hours ](*,)

Oh also it pretty much goes instantly to the point where it gets stuck, which is,

[B]Setting up locales (2.7.9-4) ...
generating locals...
en_AU.UTF-8....[/B]

I have a live CD just in case, (and I might just have to install from scratch at this rate).

Thanks for your help so far people :)

---

### Post by AdNZL on 2008-08-10
I have a sneaky suspicion I might have just figured out what went wrong. The partition I'm upgrading is almost full, ( just over a gig of free space left on it) I'm going to try freeing up some of that space and see how that goes.

---

### Post by AdNZL on 2008-08-10
Damn it I wish I'd paid more attention to learning how to use terminal :/

---

### Post by cdtech on 2008-08-10
Did you get it sorted out?

---

### Post by AdNZL on 2008-08-10
unfortunately no :(

The live cd doesn't seem to want me to move stuff from the partition I'm installing on to the safety of my other partition.

If I reinstall ubuntu I take it it will delete all the files I have sitting in that partition?

---

### Post by cdtech on 2008-08-10
correct...

---

### Post by AdNZL on 2008-08-10
bugger...

---

### Post by AdNZL on 2008-08-10
ok I managed to free up 4 gig, but so far its still sitting there doing nothing once it reaches the **Generating locals** part. worst case, I'll leave it sitting there for a few days and see if it gets anywhere.

I just can't understand why the damn things getting stuck :(

---

### Post by cdtech on 2008-08-10
Try this:
```
boot to the recovery mode
do sudo rm /usr/bin/localedef
sudo dpkg --configure -a
let the upgrade finish and when it gets to the prompt "reboot"
```

---

### Post by AdNZL on 2008-08-11
OK, I can't remember where I found the fix for this, but my brain started working for a second and I searched for "en_AU.UTF-8". I got a couple of very usefull posts, but in the end I got the system working before I even got a chance to try what they had suggested. 

I pretty much did exactly what you told me to do before I even got your post. One of the things I realised was that I could actually fully boot up as long as I was just in the terminal, and I think that helped things, although it might have just felt that way, as before I was just using the terminal option from the recovery menu. The big difference with fully logging on was that I could have multiple terminals open, which didn't seem to work from the terminal option on the recovery mode. Anyway I'm not making much sense as I really don't know what I'm talking about :P

Long story short it's working! Thank you so much for your help... now I just need to get the wireless working on my laptop :-k

---

