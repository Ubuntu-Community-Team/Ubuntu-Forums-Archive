---
title: "I need basic desktop graphics, HOW?"
date: 2010-04-17
forum: Hardware
---

### Post by bobnutfield on 2010-04-17
Hello Everyone

I am almost at a point that I believe I have a machine that will not run Linux.  There are numerous posts all over the net about the Intel 82845G integrated graphics chip.  It crashes and is unstable when it does run.  This is an older laptop with a P4 and 1GB mem that I was trying to introduce Linux to my wife because the Windows that was on it was no longer usable.

I have now tried three different distros on this machine and they have all crashed by booting to a black screen three out of five boots, or suddently crashing while using the desktop.  The closest I came to a stable desktop on this machine was with Slackware using the vesa driver.

It has been a long while since I have tried to dig into Ubuntu and there has been a lot changes.  All I want to do is minimalize the graphics requirements using the least amount of graphics for a general desktop.  No compize or any other special effects.  Just a simple 1024X768 desktop.

Can someone please give a tip on how to achieve that since there is now no xorg.conf file?  It used to be easy, now I am not so sure.

Thanks for any help or replies.

Bob

---

### Post by cascade9 on 2010-04-18
Intel 845 is hardly a great graphics chip...but it shouldnt crash like that. I've used that chipset with the intergrated video quite often, and it works. 

Possibly you have a hardware issue.

---

### Post by pi/roman on 2010-04-18
I don't know if you would like to run it without an xorg.conf (I have seen such Tomfoolery before) but you can create one by this:

sudo X :2 -configure

---

### Post by bobnutfield on 2010-04-20
I finally gave up trying get any use out of Ubuntu on this laptop.  I installed Slackware and it runs fine with the vesa driver after creating an Xorg configuration.  I tried all the workaround tricks, nothing worked.

I know it is not a great gaphics chip, but it has been around for a long time and with 128m of graphics memory, there is no reason it should not work with a distro like Ubuntu.  There was a time when I would have had a hard time finding a machine that Ubuntu would not run on.  Those days are over.

---

### Post by cascade9 on 2010-04-21
> **bobnutfield said:**
> I finally gave up trying get any use out of Ubuntu on this laptop.  I installed Slackware and it runs fine with the vesa driver after creating an Xorg configuration.  I tried all the workaround tricks, nothing worked.

I know it is not a great gaphics chip, but it has been around for a long time and with 128m of graphics memory, there is no reason it should not work with a distro like Ubuntu.  There was a time when I would have had a hard time finding a machine that Ubuntu would not run on.  Those days are over.

Its happening more and more IMO. A pity really....

---

### Post by RJQ on 2010-04-21
For a desktop for basic tasks but with solid consistency try 8.04 which still supported, I do not know how many other distros this old are around with supported repos, Ubuntu 8.04 is going for another year if I am not mistaken, that is what I use for my old machine with the intel driver.

---

