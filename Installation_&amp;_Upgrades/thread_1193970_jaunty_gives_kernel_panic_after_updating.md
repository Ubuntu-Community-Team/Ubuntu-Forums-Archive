---
title: "jaunty gives kernel panic after updating"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by quasar277 on 2009-06-22
Hi, I have an asus eee pc 900 and have installed (desktop) jaunty yesterday as wel as doing the updates, which include the kernel.
Now it won't boot up but give me this:

> 
acpi: aborted because no cpio magic
invalid compressed format (err=1)
kernel panic - not syncing: unable to mount root fs on unknown block(0,0)


I have found a way around it by quoting out the sections in /boot/grub/menu.lst that refer the new 2.6.28.13 kernel but this is hardly solving the problem.

Thanks

---

### Post by wpshooter on 2009-06-22
I would use the live CD to see if I could run a check disk on the hard drive / Ubuntu partition(s).

---

### Post by quasar277 on 2009-06-22
> I would use the live CD to see if I could run a check disk on the hard drive / Ubuntu partition(s).

I don't think that's the problem but please explain how to check disks - it's been a long while since doing that.
Btw, I can run ubuntu without problems by sticking to the older 2.6.28-11 kernel.

---

### Post by wpshooter on 2009-06-22
Is this an upgrade of Hardy to Jaunty or is this an installation of Jaunty from scratch ?  

Sounds like an upgrade from Hardy !!!

---

### Post by DNAtsol1 on 2009-06-22
> **quasar277 said:**
> I don't think that's the problem but please explain how to check disks - it's been a long while since doing that.
Btw, I can run ubuntu without problems by sticking to the older 2.6.28-11 kernel.
I've experiencec a similar problem. I have jaunty running with kernal 2.6.28-11 on my pavilion dv5 laptop and it was/is running fine on that kernal. When I was notified of the partial upgrade to kernal 2.6.28-13 I installed it and rebooted (as asked). Now I do not get as far as the log in screen. I get to GRUB and start the boot process but end up looking at a blank screen. I've simply rebooted back into 2.6.28-11 but it hardly seems like a solution. Any ideas?

---

### Post by quasar277 on 2009-06-22
DNAtsol1: it sounds exactly the same as I have. I guess we'll have to wait for the next kernel to come out.

wpshooter: it is a fresh jaunty instalation which got the normal kernel update. Should we report this bug somewhere?

---

### Post by .celleken on 2009-06-22
I'm having the same problem with that 2.6.28-13 update.

For the moment I'm booting the 2.6.28-11 kernel.

Note: This is (was) a fresh Jaunty installation.

---

### Post by wpshooter on 2009-06-22
> **quasar277 said:**
> DNAtsol1: it sounds exactly the same as I have. I guess we'll have to wait for the next kernel to come out.

wpshooter: it is a fresh jaunty instalation which got the normal kernel update. Should we report this bug somewhere?

Yes, I think I would report a bug. 

I was running kernel -11 and am now on kernel -13 and everything is as fine as a frogs hair !!!

---

### Post by Mongre on 2009-06-22
Similar issue here, new -13 kernel won't get to login screen but old -11 kernel still works fine.  Also Ctrl-Alt-F1 doesn't get me to a "terminal" session either but I can see a slight flicker on the screen so it's at least trying to switch/display.  In my case the -13 kernel option ends up locked on an almost blank screen but there are two little spots of green pixels on a single row almost at the top of the screen, each is only about 5 pixels wide so it's barely noticeable.  Reminds me a lot of problems I saw when fiddling with graphics configuration on this machine and since that took me (a relative noob) about a week to get correct I'm not about to screw with it again.  I'll just run -11 until someone finds a fix that doesn't require reconfiguring video or another update comes out.

Makes me wonder though if it has something to do with the ATI graphics driver.  I'm running a Radeon HD 4870 card with the non-proprietary fglrx driver @ 1920x1200.  Installed Jaunty from scratch.  Anything in common with the rest of you by chance?

---

### Post by quasar277 on 2009-06-23
Mongre: the -13 kernel might have more than one type of problem, I don't know. My graphics card is one of those integrated Intel thingies with shared memory.

Bug reported at
[https://bugs.launchpad.net/ubuntu/+bug/390984](https://bugs.launchpad.net/ubuntu/+bug/390984)

---

### Post by triv on 2009-06-23
I have had the exact problem as people here, I nearly got around it, but not quite.

At first I was getting the same panic message people posted here. Then I started reading about people with data corruption issues on kernel -11. So for the heck of it, I booted into my kernel left over from my 8.10 installation. Then from there I tried re-installing all the kernel packages.

After rebooting this time, the kernel booted much further and then the system locked up when attempting to start X (and there were also some modules that didn't rebuild properly like VirtualBox).

---

### Post by running_rabbit07 on 2009-06-23
Is there any relevance to types of CPU? Such as everyone that's having this problem has Intel or AMD?

---

### Post by triv on 2009-06-23
I am running the following:

CPU: Intel Q6600 Core2Quad
Motherboard Chipset: Nvidia Nforce 6 series.

---

### Post by running_rabbit07 on 2009-06-23
It can't be the chipset because I am using NVIDIA and I haven't had the kernel problem. And I also have an AMD CPU. It does appear there are quite a few people having this problem though.

---

### Post by abel.alterio on 2009-06-24
Hi,
yes, I suppose there is such a problem. I have a radeon HD3400 that was working fine until yesterday. Now I have reinstalled Jaunty: the first time I installed the ATI proprietary driver before upgrading to -13: after upgrading I could no longer log in (black screen, no ctrl+alt+F1). I reinstalled and upgraded to -13 WITHOUT reinstalling the ati driver and it works ...

---

### Post by ArGGu^^ on 2009-06-26
Hello I got the same kernel panic.

acpi: aborted because no cpio magic
invalid compressed format (err=1)
kernel panic - not syncing: unable to mount root fs on unknown block(0,0)

only if my first partition is not the root partition.

My first partition was ntfs where I have windows. so I reinstalled ubuntu and windows and now my first partition is ubuntu root partition and the last partition is the ntfs where windows is installed.
And after that the kernel -13 boots normaly.

---

### Post by running_rabbit07 on 2009-06-26
After looking at the latest post I wander if having root permissions has anything to do with it. I have my account set up as part of the root group and having full root permissions singularly. Just a guess.

---

### Post by .celleken on 2009-06-28
My specs:

AMD Athlon 64 x2 6400+
Gigabyte GA-M56S-S3
ATI 3870 (ATI/AMD proprietary FGLRX graphics drivers disabled)

Same problem, -13 won't reach the login screen.

---

### Post by quasar277 on 2009-07-11
I've tried again the -13 kernel as part of an effort to improve performance on my intel 915 graphics card (other stuff was installed/upgraded too)
and now it works!

Perhaps there was some quirkiness at instalation time.
I'm advising people with the same problem to just try it again, it might work.

By the way, it's on a eee pc-900 (intel cpu)

---

### Post by rajeeja on 2009-07-16
btw, can someone throw light on "WHY two kernals?"

---

### Post by Hogosha on 2009-07-16
i am running into the same issue. as long as i boot with the -11 kernel i am fine but i get "invalid compressed format (err=2)" with -13. I am running a laptop with an AMD Turion 64 x2

---

