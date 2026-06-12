---
title: "MN-720 adapter under Ubuntu Edgy"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by bieber on 2007-02-07
Hello, all.  Sorry to bother y'all with another wireless setup thread, but I'm having some troubles getting my MN-720 wireless adapter working on my Edgy laptop.  I thought I was done with wireless for good when I got a proper wired network in my house, but now I find myself with a laptop, for which wireless would be mighty handy.  The last thing I set up was a Linksys USB adapter on my desktop, and the process pretty much consisted of blacklisting the driver that *tried* to handle the card, but failed, then setting up ndiswrapper to replace it.  On this machine, the first thing I did was rmmod bcm43xx, which I *think* is the only thing that was trying to handle the card, but I can't remember which file I edit to blacklist it.  Then I installed ndiswrapper and the ankh drivers for my card.  Now it won't let me modprobe ndiswrapper, though: I get this ```
bieber@bieber-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
mn720-ankh      driver present, hardware present 
bieber@bieber-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```
Does anyone know what the problem is?  Also, on the last machine where I set ndiswrapper up, it didn't work with network-manager, which I didn't care about at the time because I was only ever connected to one network, but with a machine that I'll be moving about, it'd be *really* handy.  Is there any way to get network-manager to play nice with ndiswrapper cards?

---

