---
title: "upgrade 8.04 to 8.10 need help!"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by TiredBird on 2009-03-25
I have just created an upgrade of kubuntu 8.04 (kde3) to 8.10 (kde4) and am stymied by a few matters. First - some backround on the upgrade...

I have a successful installation of 8.04 which I use daily. When I first installed it on my Toshiba laptop, M45-S165, it took considerable tweaking to get the video display and the wireless interface working, but both have been working fine now for some time.

Not wanting to risk all or nothing on 8.10 with kde4, I cloned the partition containing the working 8.04 and proceeded with a network upgrade on that, expecting that would preserve the tweaking I had already done to get 8.04 to work on my hardware.

All aspects of the install went fine with no error messages or warnings. However, after the system was installed and had rebooted, the video didn't work.

I got a 'two-ball' cursor which I was able to move around with my touchpad. However, the screen was blank, except for some reddish video noise in the top part of the screen.

Looking at the ailing install from a working partition, I attempted to find the logs and see what kind of error messages I was getting. I couln't find logs that look like they came from the last boot. Everything looked like it was from the 8.04 version. 

I then looked at apt-get. In removing and reinstalling kubuntu-desktop, ubuntu-minimal and ubuntu-standard, I discovered a number of missing dependancies but I wasn't able to fix them because I couldn't get my network to work. (This is being done from the same machine but in the 8.04 partition.)

I need help! Hopefully I have enough experience so that I won't need a total hand-hold, 

Although I usually opt for the gui, I have at least a working knowledge of the command line and I can boot the 8.10 partition in single user mode. I have backup copies of nearly everything and I won't rush to conclusions. I want it to work and I want to understand why it didn't.

PLEASE! Someone at least point me in the right direction.**[B]**[/B]

---

### Post by TiredBird on 2009-03-25
I have no GUI and no network. Can someone please tell me how to find the relevant logs in the single user system (cli only)? I might be able to figure it out from there. 

It would be particularly helpful if someone would tell me how to find the assigned device names for the network components. I am writing this on the same machine and under 8.04, (using now), my wireless device is called 'ath0'. That doesn't work in 8.10.

---

### Post by norwoods on 2009-03-25
> **TiredBird said:**
> I have no GUI and no network. Can someone please tell me how to find the relevant logs in the single user system (cli only)? I might be able to figure it out from there. 

logs are in /var/log

---

### Post by TiredBird on 2009-03-26
> **norwoods said:**
> logs are in /var/log

Thanks, but that was the first place I looked and couldn't find anything that looked like it had been produced after the install. On the other hand, I did have to turn the power off when confronted with the frozen video. Maybe the log was never written...

Where specifically can I find the messages that flash by too quickly for reading during the boot process. Surely they are available for diagnostics but I have never been able to find them.

Is there a way I can stop the video, backup during the boot, or see what messages were issued by the boot process after it has failed (hung)?

Thanks in advance for your help.

---

### Post by Anthon on 2009-03-26
Try:
dmesg | less

---

### Post by TiredBird on 2009-03-29
I started over, very carefully, from a working install of Kubuntu 8.04. I spent over thirty hours and tried to follow all directions as carefully as possible. Same result. It doesn't work. 

Please do not add any comments to this thread as I am no longer monitoring it. I will start a new thread and hope that someone knows what I have done wrong and what I need to do to make it work.

---

