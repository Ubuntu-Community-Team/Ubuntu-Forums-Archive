---
title: "System instability (freeze, possibly graphics or networking related?)"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by nudel on 2007-04-22
Hi everyone,

I upgraded to Ubuntu 7.04 after having used 6.10 for a few months now. Everything was fine in 6.10, but after upgrading my system became unstable. I'm using dual boot with Windows 2000 which is still up and running so I'm guessing it's not a general hardware fault.

Problem:
With nvidia drivers installed, the system freezes after a few minutes. The mouse pointer is still movable, but nothing else appears to work. Without nvidia drivers there is no freeze, but instead the network appears to fail. It is configured and worked in 6.10 and still works in 7.04, up to the point where the system would freeze w/ nvidia drivers. At that point connection to all other machines is lost, pinging no longer works, except for pinging the machine itself. Restarting networking via "/etc/init.d/networking restart" or ifdown/ifup doesn't bring the network back up, only rebooting the entire system helps. I'm guessing that these are related problems, as the freezes always occur when networking is involved, for example when loading a page in Firefox or while using Synaptic to download a package it will happen almost immediately, although I can keep pinging other systems on the local network for half an hour or so w/o problems.
The problem persists when booting from from a live cd, either amd64 or i386 (the installed system is amd64). At first the network is up and running,  and then suddenly it stops working.

I've tried the i386 live cd on another system on the same network, with exactly the same NIC and an NV Geforce FX series card. There were no problems at all, networking was fine, everything worked.

My wild guess is that it might be some sort of hardware conflict, maybe IRQ problems? I'm not very experienced using Ubuntu or Linux in general.

To help me you will probably need more information, probably system logs or similar. Just tell me how I can help.
 
System:
MSI K8N Neo3 Motherboard
Athlon 64 CPU
NV Geforce 7600GT Graphics Card
Realtek 8029 Network Card  (ne2k-pci drivers)
Creative Soundblaster Audigy 2 Value Sound Card

Thanks in advance.

Edit: I see now that this is probably the wrong subforum, as the problem appears to be networking related. I do not know for sure though, so I posted it in the hardware category.

---

