---
title: "Wireless causing hard lock on Toshiba Laptop?"
date: 2009-07-04
forum: Hardware
---

### Post by AoSteve on 2009-07-04
Alright, here's the deal.  I can't keep my laptop stable with the Atheros chip that is inside it at all.  It's not a stability issue with the connection, however it's not really that stable...  But more or less it's the fact that after about 10-15 minutes of use on the Atheros adapter it hard locks the computer totally.  The num and scroll lock lights blink and there's nothing working with the system at all.  I have to hard reset to get back to ubuntu.

Now, the funny thing..   I call Toshiba and they say, "Well it's a motherboard problem and it'll be about $450 for us to repair it."   "Er, I'll go buy a netbook before I do that..  DEFINTELY not worth it bud."

I start playing around with it.  I notice ZERO problems while the adapter isn't connected to a network, even if it's on!  As long as I'm not connection it's all good.  Yesterday I set the thing up as a file server and copied, deleted, moved more than 400GB worth of files to and from the thing through my ethernet cable.....   NOT A SINGLE PROBLEM!?   So it's has got to be the Atheros adapter.  But it worked before, so I retrace my steps to the first time it happened.    

I updated it the other night...  I got "6" new files for it not including pidgin...  HMM   What update could cause this problem?   It worked before the updates and NEVER gave me an issue next to stability with the wireless and file transferring.  But if I want to transfer files I'll hook up to the 1GB lan to do so.   I just want my "mobil" browsing back and this has killed that ability.  I don't know how to check for the most recent updates or remove them to find out what could have caused the problem.

I've tried both the free and the restricted drivers and the same thing happens.   If I'm connected to a network whether it be my own or someone elses, it locks.  If I'm cabled in, it's fine and the machine is 100% solid.  What could cause this issue and what can I do to fix it?   I'm pretty sure it has to do with those updates that it went through a couple nights ago because I don't remember it ever giving me this issue before that.

Thanks in advance, 
Steve

System and lspci -v of Atheros adapter

Toshiba Satellite L45 S4687
Intel Pentium Dual Core 1.73Ghz T2080
2GB of ram @533mhz  (800mhz rated installed)
WD 160GB 7200rpm HDD
I believe it's an intel 931 chiptset with a 945GM display adapter

Here's the lspci -v of the card:
```

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: fast devsel, IRQ 17
    Memory at ff2f0000 (64-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: ath_pci, ath5k

```

I hope someone can help figure this out as I am stumped.

---

### Post by AoSteve on 2009-07-06
Bump, anyone? lol

---

### Post by PSUPops on 2012-05-11
I see this post is old but... Was running Ubuntu 10.04 LTS, upgraded the kernel to 3.2 and I started having the exact same problems with my wireless. Did a clean install with Xubuntu 12.04, kernel 3.2 and everything was working fine. After the recent bout of patches, I'm back to a frozen Toshiba Satellite everytime the wireless tries to connect to an AP... [CAPS Lock] blinks and the laptop reboots. Then the boot hangs and gets stuck in a reboot loop (rebooting in 30 seconds). So I try to use GRUB to cycle to the one previous kernel and still nada.
 
It pains me to say it but - Win7 doesn't have any issues with the Atheros AR8152 chipset, and that's how I'm able to write this post and research. Thoughts?

---

### Post by ahallubuntu on 2012-05-11
My solution isn't popular with everyone, but I tend to upgrade the wireless card to an Intel wireless card whenever I can in any laptop I can, because I tend to have far fewer issues with Intel wireless cards in Linux.  It's not that there are ZERO issues with Intel cards just far fewer issues than competing wireless cards.  I've yet to need to install any special driver to get one to works.

I like to buy used wireless cards on eBay, after finding out what internal wireless card is compatible with that model.  I pay about $10 USD give or take for replacement wireless cards.  Toshiba laptops should be upgrade-able pretty easily.  Just do some research on the compatible wireless cards.

---

