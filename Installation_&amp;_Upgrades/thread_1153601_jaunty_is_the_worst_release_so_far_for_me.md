---
title: "jaunty is the worst release so far for me"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by montamer on 2009-05-08
Hi
I have been using ubuntu from ubuntu 5.04
and sadly Im facing alot of problems with jaunty.

The most irritating one is that
my ubuntu freezes very frequently

I dont know wht the reason but My ubuntu suddenly freezes and nothing works :(, even ctrl+alt F1. The only way is to poweroff and on 

I have a few image processing programs which i want to run which require 5-8 days of time to run continuously. But because of this problem I have to start all over again :confused:

Is there anyway to fix it?
Im planning to revert back to Intrepid

**My system config is :**
core2duo 2.13 GHz
2 GB Ram
Intel GMA950
250 Gb sata harddisk
I have installed jaunty on ext4 partition

---

### Post by jasonsjunk on 2009-05-08
Hmmm it could be a problem with EXT4.  I know that it is relatively stable but there is still alot of testing going on.  Personally I run two storage drives on EXT4 and I have had good results with it so far but my primary partition that Jaunty is on is still  EXT3.  

Other issues could be temperature related or possibly a power supply that is drifting over time.  Do you have some sort of monitoring on the computer?  Conky is a good tool to monitor system vitals in near real time.  You might also want to check your hard drive SMART status to see if your hard drive is producing alot of errors.  I know there are tools in synaptic that allow you to test your hard drives.  I just use the built in tools in webmin to keep an eye on my hard drives.  

I don't know if this solves your problem but it gives you a few things to look at.  

BTW have you looked at the logs in /var/log ?  There might be some good info in there that can point you in the right direction.

---

### Post by karamu on 2009-05-08
I have the same issue- my system was fine in 8.04 then I updated to 9.04 (fresh install) but it often froze- as described, NOTHING worked, had to hit the reset on the front of the box.

This was happening intermittently for a few days until yesterday when it absolutely refused to boot- even in failsafe mode.

I booted with the live CD and I am unable to mount the main Ubuntu partition- I get an error message (sorry I am at work now and can't remember the wording).

Would a full format and then install again using EXT3 help at all? I liked the look of 9.04- it has the updated versions of a few packages I like to use so don't really want to go back to 8.

(Just to reiterate, I can't boot into Ubuntu or mount the drive in the live environment- what drive diagnostic tools are available to me?)

---

### Post by montamer on 2009-05-11
It looks like compiz/Intel driver is the main problem .
I disabled the Compiz and enables UXA 
No crash atleast till now :)

---

### Post by slumbergod on 2009-05-12
Jaunty is the worst release for me also. 

Not only am I having issues with video playback, browser scrolling, CPU spiking and lockups, but sound is problematic for me too. Jaunty feels like a step backward from Intrepid. 

Unfortunately, I don't have time to rollback so I will stick with it and hope all the issues are resolved. It surprises me though that so many blogs hailed this as a fanastic release.

---

