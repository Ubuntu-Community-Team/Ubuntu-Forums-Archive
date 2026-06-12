---
title: "PC wont go to to standby..."
date: 2010-06-17
forum: Hardware
---

### Post by seppl82 on 2010-06-17
Sorry for asking,
but my pc has a strange behavior.
if i like to put him to standby mode it immediately wakes up.

my mainboard is a 890 GMPro3 from Asrock


here the cut of dmesg

```
[ 1310.182730] CPU0 attaching NULL sched-domain.
[ 1310.182742] CPU1 attaching NULL sched-domain.
[ 1310.231028] CPU0 attaching sched-domain:
[ 1310.231037]  domain 0: span 0-1 level MC
[ 1310.231044]   groups: 0 1
[ 1310.231056] CPU1 attaching sched-domain:
[ 1310.231060]  domain 0: span 0-1 level MC
[ 1310.231066]   groups: 1 0
[ 1312.003054] PM: Syncing filesystems ... done.
[ 1312.031062] PM: Preparing system for mem sleep
[ 1312.031065] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 1312.031653] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 1312.035645] PM: Entering mem sleep
[ 1312.035654] Suspending console(s) (use no_console_suspend to debug)
[ 1312.090103] pm_op(): usb_dev_suspend+0x0/0x20 returns -2
[ 1312.090106] PM: Device usb8 failed to suspend: error -2
[ 1312.090107] PM: Some devices failed to suspend
[ 1312.285017] PM: resume of devices complete after 194.905 msecs
[ 1312.680127] PM: resume devices took 0.590 seconds
[ 1312.680142] PM: Finishing wakeup.
[ 1312.680143] Restarting tasks ... done.
[ 1312.810830] r8169: eth0: link up
[ 1312.862808] CPU0 attaching NULL sched-domain.
[ 1312.862815] CPU1 attaching NULL sched-domain.
[ 1312.930195] CPU0 attaching sched-domain:
[ 1312.930204]  domain 0: span 0-1 level MC
[ 1312.930211]   groups: 0 1
[ 1312.930223] CPU1 attaching sched-domain:
[ 1312.930228]  domain 0: span 0-1 level MC
[ 1312.930233]   groups: 1 0
[ 1323.160043] eth0: no IPv6 routers present
```

---

### Post by seppl82 on 2010-06-19
Is there any logfile i can provide?

I've took a look to the settings in my BIOS

Suspend to RAM is set to AUTO (cant cange it to enabled only Auto / Disabled is possible)

There is a second option i don't understand called Check Ready bit.

Any Ideas?

---

### Post by seppl82 on 2010-06-20
Okay, i've found the solution.
I've needed to disable the USB3 Root Controler. Then it worked

---

### Post by bretto_40 on 2011-02-04
Hi Sepp, thanks for posting this as I am having the same problem. Although you've now given me more of a place to look, can I please make a suggestion to help other forum members?

It is incredibly useful if, once finding a solution, posting your steps on how to complete the solution.

I don't know how to disable a USB controller, so I will now need to look somewhere else on how to do this (as I'm sure others would have to). So it would be helpful in future if you included the steps on how to 'perform' the solution.

Cheers.

---

### Post by bretto_40 on 2011-02-04
As a further follow up for other people who might have the same problem who have found this thread, before going off to look at how to disable a USB controller I had another quick search on the issue and found a thread by someone with the same issue who had tried disconnecting all their USB devices, but it didn't work, until they disconnected their keyboard.

So I disconnected my USB keyboard, re-connected it, and now suspend works, and continues to work.

So if anyone else has this issue, try the above, it may work for you.

Cheers.

---

### Post by elitenoobboy on 2011-03-18
> **bretto_40 said:**
> 
I don't know how to disable a USB controller, so I will now need to look somewhere else on how to do this (as I'm sure others would have to). So it would be helpful in future if you included the steps on how to 'perform' the solution.


You can find some more useful info that here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998)

I haven't tried the suspend modules trick yet, instead opting to blacklist the usb3 xhci thing altogether to make my suspend work (mostly), but the comments in that bug should help.

---

### Post by bluereg133 on 2011-03-18
Thanks for all of your instruction about "[B]PC wont go to to standby...". 

[/B]   Kevin

---

### Post by hane on 2011-04-06
I also have recently face same problem. However, I read all of your suggestion. Hopefully, I will solve my problem soon and let you know.



Alex:popcorn:

---

### Post by Terry Han on 2011-04-13
I am trying to get more information):P about "PC wont [B]to standby".


Hex
[/B]

---

