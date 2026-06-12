---
title: "Does Ubuntu wake up from suspend and hibernate when battery is low?"
date: 2008-06-27
forum: Hardware
---

### Post by Harry Muscle on 2008-06-27
Let's say I leave the laptop alone for a while running on battery and it goes into suspend.  A few days later (I'm guessing about the time lines), the battery starts to run low.  If I have the Power Options configured to hibernate when the battery runs low will the laptop wake up from suspend and hibernate?  Or is the low battery hibernation only happen if I'm actually using the laptop when the battery get's too low?

Thanks,
Harry

---

### Post by Harry Muscle on 2008-08-11
Bump.

Thanks.

---

### Post by sdennie on 2008-08-11
I've never seen an option to configure the machine to do this.  An alternative to this method is to use the pm-utils hybrid-suspend.  Though I've not used it, it is supposed to create resume data as if you'd hibernated the machine and then suspend it.  The end result being that the machine comes back from suspend when you bring it back up but, if it runs out of power while suspended, it can come back up as if it had hibernated when you next turn on the machine.

See:
```

man pm-suspend-hybrid

```

---

### Post by Daelyn on 2008-08-12
> **Harry Muscle said:**
> Let's say I leave the laptop alone for a while running on battery and it goes into suspend.  A few days later (I'm guessing about the time lines), the battery starts to run low.  If I have the Power Options configured to hibernate when the battery runs low will the laptop wake up from suspend and hibernate?  Or is the low battery hibernation only happen if I'm actually using the laptop when the battery get's too low?

Thanks,
Harry

It will wake up from suspend and hibernate, yes.

---

### Post by William Anderson on 2009-06-18
Hi,

Actually, no it does not. if the battery goes flat while suspended the state of the system, which is stored in ram powered by the battery, is lost and upon power up the system reboots with the same issues as if the power failed. 

The pm-suspend-hybrid option would do this by both writing out the memory state to disk as if it was hibernating, then suspending to ram. However, the pm-suspend-hybrid command does absolutly nothing on my system. It appears to need some kernel service that is not yet available in the main stream kernels yet. Sdennie, if you have pm-suspend-hybrid working, could you explain how you did this?

Hope this helps  

William

---

### Post by sdennie on 2009-06-19
I think you will need swsusp2 or tuxonice to get the hybrid suspend to work.  I don't believe the Ubuntu kernel is patched for either of those so, you might have to rebuild the kernel to get hybrid suspend functionality.  Unless of course the following contains the word "standby":

```

cat /sys/power/disk

```

---

### Post by mscir on 2009-07-27
My buddy's Sony Vaio XP laptop wouldn't boot due to a h/w problem on the m/b (digital camera RAM slot LED is always on) that stopped XP boot cold. He thought he had to buy a new machine but I installed Ubuntu on it and it boots and runs great, it runs faster than XP did, and now he's very happy and a definite convert. He definitely likes not having to hassle with an antivirus program.  

The only glitch I haven't been able to sort out is that we don't know how to wake up the machine when it's in sleep or hibernate mode. Do I have to change some settings from the CLI to enable this? 

Any suggestions would be appreciated. 

TIA,
Mike

---

### Post by kev000 on 2009-10-17
I'm testing pm-suspend-hybrid on Karmic and it returns nothing and does nothing.  I have tried it with and without tuxonice in my kernel and with the stock kernel.  Both hibernate and suspend work, but not hybrid.  Any hints?

---

