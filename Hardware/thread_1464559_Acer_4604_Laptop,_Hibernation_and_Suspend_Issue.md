---
title: "Acer 4604 Laptop, Hibernation and Suspend Issue"
date: 2010-04-28
forum: Hardware
---

### Post by DrWig on 2010-04-28
I've done a fresh install of Lucid, and although the lack of ATI X800 flgrx driver is disappointing, it's the lack of working hibernation and suspend that's the killer.

If I hibernate, the computer just reboots.  If I suspend, that seems ok, but I can't come out of it (just presents a black screen, although it seems as though the computer comes to life).

I've seen many posts on hibernation and suspend, but can't find any potential fixes or causes (I've got a swap file, and that's on and I'm not using encryted home folder either).

I don't use linux very much, mainly due to this problem persisting between versions, so I thought I'd post here!

I've attached my desmg after a hibernate shutdown/reboot if that's useful.....where do I go from here?

Many thanks

DrWig

---

### Post by DrWig on 2010-04-28
Actually, it seems the laptop doesn't reboot, the lights all flash like it#s going into hibernation, but it doesn't, the screen just goes black.

Then, if I move the mouse, the password prompt comes up.  If I log in, everything works, but the lights are still blinking like the laptops going into hibernation.

---

### Post by DrWig on 2010-04-28
another addition!  This hibernation/suspend issue has been with me since I've been trying out Ubuntu (in the last, say, three or four versions).  It's the one thing that stops me moving over, completely, to the operating system.  Other than this, lucid is very nice indeed!

---

### Post by DrWig on 2010-04-30
I'm still looking into this (I don't know allot about Ubuntu, so it's good education for me!)

I've tried this:
[http://en.opensuse.org/S2ram#Troubleshooting](http://en.opensuse.org/S2ram#Troubleshooting) 

No options worked for me

I've also tried this:
[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting) 

First two options failed, but I couldn't get a bug report to be automatically (or manually, for that matter!) generated.

Now, I'm looking in /etc/default/acpi-support and I've re-enabled ctrl+alt+backspace (one of the most useful features of old versions of Ubuntu...why on earth is it disabled...how can someone accidentally hit those three keys!)

Anyway, changing this line:
POST_VIDEO=true to false (as mentioned somewhere I've lost the link to now) did nothing

However, enabling the line:
SAVE_VIDEO_PCI_STATE=true

suspended as usual, however, restarting X (ctrl+alt+backspace) gave me the little drum motive as if everything was, indeed, working, I just couldn't see it.

....to be continued.....

I realise, no-one is interested in suspend/hibernate problems, even though, looking through the forums, they seem to be widespread and unanswered.  So I'll continue to put my meagre findings here in case they help anyone!

cheers 

DrWig

---

### Post by DrWig on 2010-04-30
> **DrWig said:**
> 

However, enabling the line:
SAVE_VIDEO_PCI_STATE=true

suspended as usual, however, restarting X (ctrl+alt+backspace) gave me the little drum motive as if everything was, indeed, working, I just could

The above seemed to be a fluke.  I can't get the laptop to suspend like this (or rather, come out of it......) a 2nd time :-(

Back to the drawing board.....I still think it's gfx related, though.....

cheers

DrWig

---

### Post by oz_ on 2010-05-02
I posted something that might be related.

[http://ubuntuforums.org/showthread.php?t=1468190&highlight=suspend+issue](http://ubuntuforums.org/showthread.php?t=1468190&highlight=suspend+issue)

have you found a solution for this?

---

### Post by DrWig on 2010-05-03
not yet.  Found quite a few people with open issues, but no firm solutions.  None of the stuff I tried above worked, and Ubuntu doesn't know anythings gone wrong, so doesn't report a bug etc..

I'm gonna keep looking, though!

cheers

DrWig

---

### Post by DrWig on 2010-05-03
Found this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711) 

Looks like someone else is chasing down a similar issue.  It also points to this article:

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) 

At last, a way forward!  I will try later in the week and report back....

cheers

DrWig

---

### Post by oz_ on 2010-05-03
well, 
I guess its a start

---

### Post by pmos69 on 2010-05-03
> **DrWig said:**
> Found this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711) 

Looks like someone else is chasing down a similar issue.  It also points to this article:

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) 

At last, a way forward!  I will try later in the week and report back....

cheers

DrWig

Yes, I filled that, but it's still not assigned to anyone.
Hopefully when that happens something will come out of it.

Maybe if enough people register saying the bug affects them also it can draw more attention.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711/+affectsmetoo)

---

### Post by DrWig on 2010-05-04
registered that it affects me too....didn't see that button ;-)  New to this bug reporting lark.....

cheers

DrWig

---

### Post by SyAu on 2010-05-26
Its working for me and others also finding the same.

Please see this thread,

[http://ubuntuforums.org/showthread.php?t=1469340&page=4](http://ubuntuforums.org/showthread.php?t=1469340&page=4)

---

### Post by DrWig on 2010-05-27
Thanks for the update.....will try this today

---

