---
title: "Marvell 88E8056 traffic after shutdown"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by cosmix64 on 2007-07-27
Ok here's a pretty weird problem with an Asus P5B Deluxe and Feisty w/ all updates installed. This board has two gigabit ethernet controllers, the PCIe 88E8056 and the older PCI based 88E8001. The former is typically handled by (fully open source) sky2 or (the semi-closed Marvell-provided) sk98lin and the latter by skge. Now here's the problem.

Until a couple of weeks go I was using the older PCI-based 88E8001 on-board Gigabit ethernet controller with the ubuntu-included module without any problems. At that point I thought I'd give the newer PCIe 88E8056 controller a try, as Feisty was supposed to include a newer version of the sky2 module that properly supported it.

What I discovered doesn't really have to do with sky2 or sk98lin but with a very weird behaviour that the controller exhibits when the computer is shut down: For the first 15 seconds after shutdown completes and the computer is powered off, the interface remains on (as evidenced by the LEDs on the connected switch). After the 15th second the interface starts transmitting packets --- unfortunately my switch is of the cheap unmanaged variety and I cannot really tell what it is transmitting --- incessantly until the computer is switched back on again and the card reset by the BIOS. What's weird is that this is not supposed to happen in any case, even if Wake-On-Lan (WOL) is turned on. Now, I've disabled all 'wake on <activity>' options on the BIOS and I've also tried (successfully judging by the lack of any error messages) disabling WOL using ethtool. This behaviour persists.

I'm using sk98lin for the time being, as I've read that some problems with sky2 persist, although I haven't noticed any instability or network performance degradation using either driver, while the computer is on. 

The problems start when the computer is turned off. The 'traffic' the interface transmits however seems to cause my networked devices on that switch to lose connectivity after a period of time requiring either the disconnection of that machine or a reset of the switch. I have no idea what is causing this constant stream of data (or what it contains) and I can't think of something that would fix it. It seems that the linux driver is not properly setting the power state on the card, although I can only guess that this is what happens; ethtool seems to have no effect on this.

I'd appreciate any pointers, ideas, tips, etc. if you have any.

Many thanks.

---

### Post by maiken on 2007-08-10
Hi cosmix64,

No solution, just commiseration; I am experiencing what sounds like an identical problem on a freshly built machine running Feisty Fawn on an MSI G33M motherboard with an onboard Marvell 88E8056 NIC. This has been a source of great frustration for me; when this first happened I thought my switch had chosen an inopportune moment to die, since, just as you describe, other machines on the same switch lose connectivity when the 88E8056 controller start acting up, a short while after shutdown.

Since my board is from a different manufacturer, it sounds like we can eliminate any WoL BIOS features as the source of the problem?

I have switched from the sky2 driver to a freshly built version of sk98lin straight from the Marvell site but the behavior persists. My controller takes rather longer than 15 seconds after shutdown to start acting up, but once it does, it takes down the switch it is connected to. My machine happens to have a power supply with a switch, so I have taken to cutting power to the motherboard after shutdown to prevent this machine from poisoning the network, but this is not an attractive long-term solution.

Like you, I assume the Linux driver is leaving the 88E8056 controller in an odd state that causes it to lose its mind a short while later. If anyone has any suggestions for tinkering with either the sky2 or the sk98lin drivers' management of the NIC's power state and/or the state it leaves it in at shutdown, pointers would be much appreciated.

---

### Post by cosmix64 on 2007-08-10
> **maiken said:**
> 
Since my board is from a different manufacturer, it sounds like we can eliminate any WoL BIOS features as the source of the problem?


The brand of the board is irrelevant here. Different board does not mean completely different BIOS. Nevertheless, I agree that it doesn't seem to be related to Wake on Lan. 

> 
Like you, I assume the Linux driver is leaving the 88E8056 controller in an odd state that causes it to lose its mind a short while later. If anyone has any suggestions for tinkering with either the sky2 or the sk98lin drivers' management of the NIC's power state and/or the state it leaves it in at shutdown, pointers would be much appreciated.

Have you tried submitting a bug report on this to launchpad or elsewhere? Since sk98lin is provided by Marvell themselves I'd like to believe that they'd have taken care to properly manage the controller, even if the actual driver is based on the open source one; which makes it even weirder.  Do you run other operating systems on that machine? If you do it might be a good idea to post your experiences with it under, say, Windows XP or Vista.

---

### Post by maiken on 2007-08-10
> The brand of the board is irrelevant here. Different board does not mean completely different BIOS. Nevertheless, I agree that it doesn't seem to be related to Wake on Lan.


OK, fair enough. the MSI BIOS I'm running at the moment is branded "v02.61 (c)1985-2006, American Megatrends, Inc.". Does this sound anything like the BIOS for your Asus?

> Have you tried submitting a bug report on this to launchpad or elsewhere? Since sk98lin is provided by Marvell themselves I'd like to believe that they'd have taken care to properly manage the controller, even if the actual driver is based on the open source one; which makes it even weirder.


I haven't submitted a bug report anywhere yet; have you submitted one I could add to? I also found it strange that the manufacturer's own drivers would mismanage the shutdown of the adapter.

> Do you run other operating systems on that machine?


No, just Feisty.

---

### Post by maiken on 2007-08-10
Update: I blame NetworkManager.

I noticed when switching between sky2 and sk98lin that it was difficult to properly shut down my eth1 interface: it would spontaneously reactivate itself. That is, if I ran

```
sudo ifconfig eth1 down
```

then, say

```
sudo rmmod sky2
```

I would be told that sky2 was still in use. The system logs showed that immediately after I brought down eth1, it brought itself back up again. I could work around this by unplugging the network cable before bringing down the interface; then it would stay down, allowing the driver module to be unloaded. This felt like the work of NetworkManager trying to preserve connectivity "intelligently", so I disabled NetworkManager as per [this page]("https://help.ubuntu.com/community/WifiDocs/NetworkManager").

Voila; now, after shutdown, the NIC's activity lights are no longer lit, and it does not poison the switch it is connected to.

So at the moment, my theory of the root cause is:

[LIST]
[*]NetworkManager is overzealous in trying to preserve connectivity
[*]At shutdown, NetworkManager prevents the NIC from being shut down properly by trying to reactivate it immediately
[*]This sequence just happens to leave this particular controller in an improper state where it misbehaves
[/LIST]

For a wired-network desktop machine, I saw no value in NetworkManager, so I have removed it. Independently of this problem, it seems like a bug in NetworkManager that it would interfere with bringing down interfaces at shutdown time.

Please let me know if you can confirm any of this on your machine.

---

### Post by cosmix64 on 2007-08-10
Before I proceed let me thank you for looking into this -- I wouldn't have bothered due to lack of time (and the second gigabit interface on that board that worked fine), but since you started it let me add some more info. 

1. I have also noticed the interface reactivation less than a minute after an 'ifconfig down'. 

2. In order to try and investigate further I tried uninstalling (purging) network-manager from the system as opposed to disabling it. To my surprise the behaviour persisted when I shut down the machine and also after the first reboot. Rebooting the machine for a second time worked and the interface now turns off upon shutdown -- this was perhaps related to the controller hardware state rather than the software (all reboots were 'warm'). Network manager may be the culprit as per your findings, although I suppose since other controllers don't behave like this there might be a need for a driver fix on this one. 


It might be a good idea to file a bug report on launchpad and provide a link here for future reference. I'll certainly confirm your findings.

Thanks for your effort and time spent on this.

---

### Post by maiken on 2007-08-10
Aha -- so, just to be clear, you do not see the autonomous link-reactivation behavior with the other controller, just the Marvell one?

If that's the case, it seems like this might be an issue of NetworkManager and the driver interacting badly. In particular, I've been wondering whether the Marvell drivers report the NIC's link-status even after the interface has supposedly been brought down. It looks like NetworkManager gets a report of a live but unused link and enthusiastically brings it up.

I'm glad we got somewhere with this; it was pretty baffling. I'll sniff around the Marvell drivers a little more to see if I can prove or disprove the idea that they're reporting information to the OS after a link has been brought down, and either way, I'll plan to file a launchpad bug.

---

### Post by maiken on 2007-08-10
And, you're welcome for the time. How nice of you to say so :)

---

### Post by cosmix64 on 2007-08-10
Both NICs are Marvell. As I wrote in the original post on this thread this board comes with two onboard NICs. One is PCIe based (the 88E8056) and the other is PCI based. Both chips are made by Marvell :)

The one I used until now was the PCI-based one, a Marvell 88E8001. That NIC worked absolutely fine with Network Manager. The reactivation was probably there; the post power-off traffic frenzy wasn't. 

I'll be so bold so as to argue that this is a driver issue here rather than a NetworkManager issue. I agree that NM is taking the interface up, but the driver should handle this properly when shutting down the system. It is not NM's responsibility to handle the state of the hardware. The driver is most probably not leaving the NIC at a proper state. 

What we've found is a workaround, not a solution I'm afraid. Let me know of the bug # when you do file it so that I can confirm/add to it.

Regards.

---

### Post by maiken on 2007-08-10
OK, thanks for the clarification.

I was thinking that if the 88E8001 does *not *auto-reactivate, we may have a fairly specific thing to blame the 88E8056 driver for: it may not shut down the NIC in the way the rest of the system expects (causing the NM to try to bring it back up). If the 88E8001 *does *auto-reactivate, then we have only vague suspicions about what exactly the 88E8056 driver may be doing wrong.

---

### Post by cosmix64 on 2007-08-10
Let's qualify our terms here so that we are clear. The 88E8001 worked fine with NM. I don't remember whether the interface was brought up by NM if you tried ifconfig down because I never tried it. This is what I meant with 'auto-reactivate'. In any case this has nothing to do with the driver; it's NM-specific.

Now, I don't remember whether the interface was left on or not after power-off. In any case, in the year or so that I used it I never had any problems with post power-off traffic. 

Regards.

---

