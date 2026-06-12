---
title: "Connecting multiple hard drives"
date: 2013-04-20
forum: Hardware
---

### Post by pimaster on 2013-04-20
Sorry this isn't much to do with ubuntu but there is such good support on this site. I have a few computers and thus a few hard drives. In an ideal world I would have all of the hard dives externally stored (each with a different OS on them) and connect the to some kind of switch box, then be able to switch which computer is running which OS  I don't want/need to switch whilst active but I would like it so that I could run an OS needed for a reason such as internet use, or gaming or messing around with Linux running on the fastest pc, while on a different running pc I could play music or search the web. Also, could I install the drivers for all of the computers even though it is not using all of the hardware at any one time? (Mainly for a windows hard drive)

Sorry that it isn't much to do with Ubuntu but any help would be massively appreciated. :)

---

### Post by dabl on 2013-04-20
One issue with hard drives is that you are limited to the number of SATA connections on the motherboard, unless you add a PCI SATA expansion card (which may not let the connected drives be seen by BIOS as bootable).

For Windows gaming, you need a native Windows installation on the hard drive of the fastest PC with the best video that you have.

Setting aside that case, if your objective is to have a reliable Linux system with multiple OS choices, then why not install either VMware Player or VirtualBox, and have as many VMs as you want?  Here I have siduction (KDE 4.10) on the SSD, and 4 VMs:  Kubuntu 12.10, Kubuntu 13.04, siduction RazorQT, and Windows 7.  But I'm not a Windows gamer.

Another direction is to use USB flash drives, and use unetbootin to install a Linux Live ISO.  Parted Magic, for example, is one that really comes in handy at times.  ;-)

---

### Post by alhefner on 2013-04-20
If you want your hard drives to be external, put them in an external case (individually) that has a USB interface. Then, you can load each one with the OS and file system that OS needs. Once you do that, just change the BIOS settings to boot via USB first and then, you're set. On power up, the BIOS will look for a hard drive on the USB. If it's not there, it will boot from the internal drive. That's how I'm set up to boot Ubuntu now.

---

### Post by pimaster on 2013-04-21
What I want, is to be have about 4 different operating systems, each on their own hard drive so that I can connect the operating system I want to use to a computer. This is because I want to run any two operating systems at any one time, if I dual boot two computers it gets complicated with multiple versions of the same OS, would I need two computers identicle in hardware to do that, and could I keep all of the hard drives in a case, or a draw and use this to boot up the OS I want:
[http://www.amazon.co.uk/StarTech-5-25-Mounted-Drive-SATADOCK525/dp/B003D1CULU/ref=sr_1_16?ie=UTF8&qid=1366542404&sr=8-16&keywords=5.25+dock+bay](http://www.amazon.co.uk/StarTech-5-25-Mounted-Drive-SATADOCK525/dp/B003D1CULU/ref=sr_1_16?ie=UTF8&qid=1366542404&sr=8-16&keywords=5.25+dock+bay)
Would all components in the computer have to be the same or could I have one with a better processor and ram, and still be able to boot a windows or linux from either pc? Also is booting an OS slower on a usb stick?
Thanks :)

---

### Post by dabl on 2013-04-21
That won't work at all for Windows, because of GWA.

For Linux, your main problem will be different hardware (ethernet chips, GPU, and sound chips).  And both CPUs the same architecture, or else you can only run 32-bit.  You can usually connect a hard drive with a working Linux system to a second computer and fix any driver issues manually, but I don't know how that can be automated in a "mix 'n match" kind of way.

To reiterate, a Linux OS with a another OS on a VM is probably the best way to do what you want to do, unless you have a pair of identical hardware platforms.

---

### Post by pimaster on 2013-04-21
So if I did have a pair of identical PCs would it work; could I boot up from one, shut it down, swap the hard drives over and boot from the other pc? Would I have to buy the components at the same time, and would a graphics card in one and built in graphics in the other make a difference? Is it just the motherboard and ram that have to stay the same, could a use a different processor, e.g. 3rd gen i3 and 3rd gen i5, or two different model of the Intel Celeron based around the same CPU architecture?
Thanks a great deal :)

---

### Post by CatKiller on 2013-04-21
It doesn't have to be the same processor, just the same type, so both x86 and both 32-bit or both 64-bit. RAM doesn't matter and graphics won't be an issue if you're using open-source drivers: proprietary drivers will screw you up. You'll probably get an expanding list of ethernet devices, and sound devices.

Virtual machines are definitely the sane choice. It's pretty much what they're for; a standardised set of abstracted hardware that you can move around at will.

---

