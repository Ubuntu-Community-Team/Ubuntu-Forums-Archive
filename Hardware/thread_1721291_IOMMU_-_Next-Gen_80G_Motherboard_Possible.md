---
title: "IOMMU - Next-Gen *80G Motherboard Possible?"
date: 2011-04-04
forum: Hardware
---

### Post by GraysonPeddie on 2011-04-04
Hi, everyone. I am wondering if the next generation AMD motherboards with built-in graphics chipset will support IOMMU for PCI passthrough? I'm unsure if my ASUS M4A88TD-V EVO/USB3 AM3 motherboard supports IOMMU as I want MythTV to be in a virtual machine and have access to my ATSC TV tuners and be separate from my main host system, which will then allow mySQL database (once I migrate the SQL recordings) and mythweb (Apache server) to reside in my MythTV virtual machine.

The reason why I ask the question is because in my Ubuntu 11.04 (Beta 1) home theater PC with MythTV frontend, doing dpkg-reconfigure mythbuntu-repos allows me to select 0.24 or 0.25 and I'd like to try out 0.25 just for a test drive, but in Ubuntu Server 10.04 LTS (can't upgrade due to [problems with bridging wlan0 with eth1](http://ubuntuforums.org/showthread.php?t=1598164)), I only have 0.23, 0.23.1, and 0.24 and not 0.25, so I am left with staying with 0.24 until I get a new motherboard that supports IOMMU. I am going to wait until 12.04 LTS, hoping that I won't have any network bridging problems with hostapd/wlan0 (although my issues with network bridging in 10.10 and later does not belong here, though).

Also, while not related to my thread, what are the memory requirements when I run as my master backend server? Do you think 256MB will be as low as I can go? I have 8GB of system memory and I gave Windows Server 2008 R2 trial 2GB of RAM and my Windows Server is running so fast, like during startup/shutdown times.

---

### Post by GraysonPeddie on 2011-04-06
Hello, everyone. I'd like to let you know that current-generation 8xx chipset (probably except for 890FX) does not support IOMMU.

My advice for those who want to virtualize a TV tuner in a virtual machine is to get a SiliconDust HDHomeRun. I currently have a Hauppage HVR-1250 ATSC TV Tuner; I bought the tuner as I'd like to integrate the tuner into my server, as I don't want a separate box like the HD HomeRun. It could be pretty useful just to buy a gigabit NIC and a gigabit switch for multiple HDHomeRuns, but if only I could organize HDHomeRuns neatly and cleanly if I have 2 or more of HDHomeRuns.

Otherwise, I'll just sell my 880G motherboard and buy an 890FX motherboard with an AMD Radeon 5450 (downclocked where I can get the power consumption down to 1W in idle mode) even though the 890FX is overkill for server use since I don't need Crossfire support. But then it'll be troublesome to swap out all the parts, so the HDHomeRun may be the only option if I want to run MythTV as a master backend in a kvm-based virtual machine.

Here's the source about IOMMU:
[http://www.amdzone.com/phpbb3/viewtopic.php?f=52&t=137489&start=0](http://www.amdzone.com/phpbb3/viewtopic.php?f=52&t=137489&start=0)

Thanks for those who are trying to help even though I have not received a response. :)

---

