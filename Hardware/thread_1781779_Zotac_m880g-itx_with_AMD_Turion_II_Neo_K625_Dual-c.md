---
title: "Zotac m880g-itx with AMD Turion II Neo K625 Dual-core"
date: 2011-06-14
forum: Hardware
---

### Post by suleyman_snk on 2011-06-14
Hi all,

I am trying to build a NAS for home and checking low power Intel or AMD mother boards. 

Goals: 

To have low power consumption
To run Ubuntu (ubuntu or xubuntu)
To have at least 4 SATA disks but will add 2 more disks in the future (disks will be green)

By some search, I found ZOTAC M880G-ITX MotherBoard with AMD® Turion™ II Neo K625 Dual-core CPU providing 6 SATA interfaces. Searches also showed that this CPU is performing better than Intel Atom D525. So I am interested in this setup. 

Anybody have any information about Ubuntu compatibility of this setup?

Or any experience on similar configuration is more than welcome :)

Thanks in advance. 

-Suleyman

---

### Post by Bradburts on 2011-06-15
Hi,
I have an Atom D510 and that uses 30W with Samsung F4's spun down, 40W with everything ready and upto 50W during boot. I have installed Gnome while I learn & so I may achieve less headless.
This 30W is a long way off the Atom's 13W TDP and 4 W chipset datasheet claims. Be careful with datasheets they often lie :(.
What suprised me is that the rubbish ITX case PSU I am using draws 3.6W when the PC is off. My meter may be a little out, the lowest I have seen is 2 W from an old 12V brick unloaded, Even if the true figure PSU figure is 2W thats a couple of tins of beer over the year and wasting beer is serious stuff in my book.
I could not find a true low power Atom motherboard outside off the embedded market (where the price may be £300 or more) or the netbook market.
I choose a D510 as I thought I wanted RAID 1 and the mobo was cheap. The D series has 2 SATA ports where as the netbook Atoms only have 1 SATA.
I am comming to the opinion that I may not need the 2 SATA ports rather just one big drive and USB drive for backup using flexRAID. Maybe music and photo would work well on USB.
Once I have finished learning I may start again and rip up a netbook. 
I would be interested in what you find and how it goes for you. 
 
EDIT
I am now using a picoPSU and the board is now running @ 27W. With both hard drives spun down I get 19W.
Off is now 2W.
So make sure you get a picoPSU if you want low power.

---

### Post by Yellow Pasque on 2011-06-15
I have an 880G and Phenom II N660 (same 'Champlain' core as your CPU) in my laptop. Ubuntu 11.04 runs very well on it except for suspend/resume.

---

### Post by s5narl on 2011-06-17
Hi Suleyman,

I'm using the same board, and used the last PCIe slot to insert another 2x Sata ports.  I did the following:

1. Installed 6 x 2TB hard drives into the motherboard sata ports;
2. Installed a bluray drive, and a 160gb drive into the PCIe sata ports;
3. Installed Ubuntu Server;
4. Raided the 6 x 2TB hard drives, for a Raid 5 configuration, for 10TB of storage;
5. Also installed webmin + kde + xbmc + pyload + transmission

This works, but required a lot of tweaking.  You will need to obtain the latest AMD/ATI drivers to get this to work properly.

Although green drives may sound like a good idea (and I initially installed them in my system), the performance is extremely poor.  I would suggest a higher/better spec hard drive, and to mount them using NFS, as Samba seems to have a bug that lowers performance significantly.

Also, if you are using this as a home theatre pc, then be aware that the integrated sound on this board does not seem to be able to stream 5.1 sound over hdmi.  You will need to use an optical cable to stream 5.1 sound to a home theatre receiver.

Anyone else had any experiences to share with this board?

---

### Post by cascade9 on 2011-06-18
AMD Fusion should have slightly lower power requirements than Atom, and have a bit more CPU grunt. 

Fusion is still pretty new though, it might not get full linux support till kernel 2.6.39/3.0+. The only issue I could see with fusion now would be the intergrated GPU though, everythign else should work 100%.

---

### Post by s5narl on 2011-06-19
I would agree with cascade9 from my personal experience.  While most things work, there seems to be some bugs relating to the integrated GPU:

1. Shifting between video modes - when I exit XBMC, the video screen will become garbled;
2. power saving seems to be broken in some instances.  In particular, when the system goes into sleep mode, and the receiver is off, the monitor/screen will not re-activate when it comes out of sleep mode.  I hear the drives spinning up, but nothing is on screen.

Despite these bugs, I'm pretty happy with the system, as it has enough horsepower to handle htpc + server duties. 



> **cascade9 said:**
> AMD Fusion ... ...

Fusion is still pretty new though, it might not get full linux support till kernel 2.6.39/3.0+. The only issue I could see with fusion now would be the intergrated GPU though, everythign else should work 100%.

---

### Post by Bradburts on 2011-06-20
Has anyone measured the power used by the Zotac m880g-itx with AMD Turion II Neo K625 Dual-core and in what configurations?
I would really like to know!
The board looks great and has a lot of features. The board seems well suited for a home media system.   But what about power use?

---

### Post by suleyman_snk on 2011-06-22
Thanks a lot for all responses.. I got my answer for this specific topic: Ubuntu is running perfect on this platform, may be with some tweakining.

But now I need to have Virtualization support on this server(probably with XEN or KVM). Anybody has experience virtualization on this platform? I heard rumors such that performance is not enough for virtualization. So real experiences are very valuable for me. 

I am not expecting production performance, this is a home server. But I want to run one virtual server to act as a HOME NAS, one other as a Web Server, may be one other as a mail server. Of course I may want to have some test platforms but these are not critical, will not be up and running all the time and performance is not an issue. But for NAS, Web Server and Mail Server, all three will run 7x24 and should perform well. 

Of course I will have enough memory for them but I am afraid of CPU performance. 

Any idea?

---

