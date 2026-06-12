---
title: "New Ubuntu Build!"
date: 2010-12-03
forum: Hardware
---

### Post by steve7777777 on 2010-12-03
I'm going to build a new PC for Ubuntu (and occasionally Win7 - VMware virtual machine only). The PC will be used as HTPC, and also for a 2TB Samba share running 24x7.

Hardware:
*Phenom II X4 965 Black AM3 3.4Ghz 512KB 45NM 125W 
This is a "V" processor so will run virtual machine efficiently. I'm open to other suggestions!
*[ASUS M4A88T-M/USB3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131660") AM3 AMD Micro ATX Motherboard
For the HTPC I have a 32" LCD 72p TV with plain old stereo speakers, so I assume the on-board video will suffice.
*memory - a single 4GB DDR3 for future up-gradability or  2GBx2 

Questions:
Based on my needs should I go with 32 or 64bit Ubuntu?

For 32bit Ubuntu how much total DDR3?
For 64bit Ubuntu how much total DDR3?
Thoughts on only 1 stick ? I realize a pair is better but can take a slight performance hit.
Other MB's to consider? I'd like USB3 and decent on-board video and of course no driver problems with Ubuntu.

I installed Ubuntu on a test machine, Intel 2Ghz/1GB ram and everything is working  - Samba, etc. so ready to make the switch from Windows. I'd appreciate any comments or suggestions and will order soon! 
Thanks

---

### Post by luke0927 on 2010-12-03
Thanks for posting this I'm looking for Ideas too I want to build a PC to put Vshpere on then run Ubuntu and whatever else I need.

Where you going to do ESX/Vshpere or just workstation?

---

### Post by steve7777777 on 2010-12-03
I should have searched more. I found this thread:
[http://ubuntuforums.org/showthread.php?t=1600771&highlight=Phenom+II+X4+965](http://ubuntuforums.org/showthread.php?t=1600771&highlight=Phenom+II+X4+965)

...answered some of my questions.

---

### Post by cchhrriiss121212 on 2010-12-03
Running that machine 24/7 is going to give you a big electricity bill, if you are not doing anything intensive that CPU is overkill. 
Avoid ATI graphics and get Nvidia instead, they are far superior in every way.

---

### Post by steve7777777 on 2010-12-03
> **UnbeatableMachines.com said:**
> You are going to want to go with 64 bit, especially if you want to one day have more then 4 gigs of ram. That processor might be a little over kill for what you are using it for, but if your doing VM maybe not. Otherwise looks good but go with 64 bit for sure.

Thanks, yes I'll go with 64bit and 8GB ddr3.

---

### Post by steve7777777 on 2010-12-03
> **cchhrriiss121212 said:**
> Running that machine 24/7 is going to  give you a big electricity bill, if you are not doing anything intensive  that CPU is overkill. 

Yeah, I know but will underclock


> **cchhrriiss121212 said:**
> Avoid ATI graphics and get Nvidia instead, they are far superior in every way.

I'm going with on motherboard gpu. Can you suggest an alternative MB with Nvidia?

---

### Post by cchhrriiss121212 on 2010-12-03
If you are planning to underclock, then why not just buy a cheaper CPU? The 965 you have listed above uses 125W, whereas regular CPUs use only 65W. 

I don't have any specific recommendations for boards, ASUS make good ones and any of them with USB3 will have a decent onboard Nvidia GPU.

---

### Post by steve7777777 on 2010-12-06
> **cchhrriiss121212 said:**
> Running that machine 24/7 is going to give you a big electricity bill, if you are not doing anything intensive that CPU is overkill. 
Avoid ATI graphics and get Nvidia instead, they are far superior in every way.

I did some searching to on the Nvidia vs. ATI issue and found what you already know - for Linux Nvidia is better than ATI for HD video playback - 1080p / h.264. The only MB that I've found that meets most of my specs is the MSI NF750-G55 AM3 NVIDIA nForce. What it lacks is USB 3.0. Another option to skip the on-board video and get a cheap Nvidia 8400GS or G210 gpu. 

For CPU I'm now looking at an AMD Athlon II X4 640 Propus 3.0 GHz. I think for my needs it should be ok and it's 95w for 24x7 operation.

I'd appreciate any suggestions/comments but I'll be ordering soon.

---

### Post by cchhrriiss121212 on 2010-12-06
Sounds good to me. The only other thing to add is that there will be a new line of CPUs (Intel and AMD) coming out early next year, so you might consider waiting until then when there will be price drops on older models.

---

