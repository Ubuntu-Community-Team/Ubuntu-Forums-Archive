---
title: "Major Hardware Upgrade- Reinstall Necessary?"
date: 2012-05-03
forum: Hardware
---

### Post by jamesbeat on 2012-05-03
I have been given an old Dell Dimension 4300, and was delighted to discover that this machine has a lot of upgrade potential.
It seems that I can replace the 1.6Ghz P4 processor with up to a 2.8Ghz one, and up the memory from 512Mb to 1024Mb, which should give me a system that will be useful for a while, and at extremely low cost.

What I'd like to know is if making such a big change to the specs (including a bios update) will require a reinstallation of the Ubuntu 10.04LTS I currently have running on the machine?

My guess is no, but I wanted to be sure, as there may be factors involved that I haven't considered.

---

### Post by ahallubuntu on 2012-05-03
Ubuntu 10.04 LTS had major issues with certain Intel integrated graphics chipsets, including the 845 chipset in your new 4300.  I would assume that to use your old drive in 4300 you would need to add an AGP graphics card (if there isn't one already).  Otherwise, I'd expect serious reliability problems like freezes and graphics issues.  But AGP graphics cards aren't too expensive.

I have upgraded CPU and RAM on a few similar Dimension desktops (I put 11.04 on them successfully - problems with the 845 seem fixed by then).  Here are the specs on yours:

[http://support.dell.com/support/edocs/SYSTEMS/dim4300/specs.htm#1101572](http://support.dell.com/support/edocs/SYSTEMS/dim4300/specs.htm#1101572)

Notice that Dell lists the CPU FSB as 400MHZ.  That limits your CPU upgrade choices.  First of all, you're probably limited to a Northwood (not Prescott) Pentium and the 2.8GHZ CPUs with a 400MHZ FSB are more expensive (probably eBay) than the cheaper ones with 533MHZ FSB.  Make sure you upgrade the BIOS to latest (use Windows if you can) before trying to upgrade the CPU.  You have to get a socket 478 CPU as well.  Look for a full list of P4 CPUs on Wikipedia.  Any desktop socket 478 Northwood P4 with 400MHZ FSB should work.

Also, this Dimension unfortunately uses SDRAM not DDR RAM.  And the max RAM listed is 512MB not 1GB.  Sometimes Dell's specs are wrong and you really could upgrade to 1GB - but I have had issues with 512MB SDRAM DIMMs.  (whereas I've had few issues with DDR).  

Based on the AGP card and the limited RAM as well as possibly the limitations on the CPU, I'd say this one really isn't worth spending much money to upgrade.  With an AGP graphics card, though, your existing Ubuntu 10.04 LTS drive probably will work, though.  But I'd look for a newer tower myself if possible.

---

### Post by jamesbeat on 2012-05-04
The processor that I ordered does have a 400Mhz fsb, and is confirmed working on this model.
I don't quite understand what you are saying about the graphics card. 
As I understand it, integrated graphics means that the motherboard has onboard graphics?
If so, then that is not the case. My motherboard does not have integrated graphics, but it does have an AGP graphics card installed, a ATI Rage 128.
Also, the specs published by Dell are just plain wrong. The machine is definitely capable of using up to 1Gb ram. The rumor is that they lowered the specs because Windows was having problems when a full Gb was installed.

I'm not really concerned with the hardware side of things, what I want to know is whether I should do a clean install of Ubuntu after performing the hardware upgrades, or is it ok to keep my current install?

---

### Post by ahallubuntu on 2012-05-04
According to the specs, you could use Windows on this computer without that AGP graphics card - just use the connector for the integrated graphics instead.  But the AGP card you apparently have will be faster/better even in Windows.  Still, you'd have the choice - and not every Dell would have that AGP card installed.  Lucky for you, yours does.

In Ubuntu 10.04 you really would NOT have the choice - because with the integrated graphics controller does not work well with Ubuntu 10.04.  But if you have an AGP card, you should not have the graphics issues.  I could not know or not whether you had the AGP card installed before you confirmed it.

Should you re-install?  My answer is easy: try it and find out.  If it works, you are good.  If not, re-install.  FYI, I have used the same Ubuntu image for many different types of hardware.  Ubuntu is very portable between different hardware.  My guess is it will probably work fine for you on this new computer without re-installing.

---

### Post by jamesbeat on 2012-05-04
That's weird, I have had this machine apart, and it definitely has no onboard graphics; there is only one output, and that is on the AGP card.
I have ubuntu up and running on it already, just wanted to know if there would be any disadvantage to keeping the same install after upgrading the bios, processor and memory.
I'm glad that it will not be necessary, because it would be a real inconvenience as I have a lot of files that I would have had to transfer.

---

### Post by mips on 2012-05-04
Upgrading the hardware will work fine, it's only the cpu & ram. NO reinstall required.

---

