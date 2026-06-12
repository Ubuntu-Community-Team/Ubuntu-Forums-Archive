---
title: "Need help with install on a Compaq Armada E500"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by chuckinKC on 2005-05-03
Hey everyone
First time Linux install, and I don't want Windows anymore.

I have a compaq Armada E500.  I am trying to do a basic install and it keeps hanging up at this line

Freeing unused kernel memory: 224k freed

and it just sits there...

I am just starting out, and I have no idea where to look or how to work on this problem.  Please help!

---

### Post by WayneLeutwyler on 2005-05-04
Take a look here: 

[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsCompaq](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsCompaq)

Looks like someone tested the E500 with Warty. 

You might try to boot the install with this option. linux noapic

Report back with your results. 

Wayne

---

### Post by Daveski on 2006-10-23
FYI I have Dapper installed on a 256Mb E500 (UK).
Installed without any problems and all seems to be working fine. I have not tested IR, Modem or TV out, but power management seems to work as does sound etc.

---

### Post by jmagsho on 2007-02-08
I too have Dapper installed on an E500.   I had issues with the install initially and it took a few tries with the CD before I got it put down properly; however I believe it may have been the fact that the machine only had 128mb or Ram at the time, and I think the bare minimum to get an easy install via CD is 192mb.  Keep in mind that many of these machines came standard with only one 64mb stick of ram...

I have since upgraded to 512mb (the low density sdram chips for these machines are expensive, but look around on Ebay - I scored a two 256mb chips for $39 (US) each.

The machine flies with the added ram, and I've got it running with a Netgear WT511 wireless card using Automatix2.

It's possible to have a solid system on this hardware, so good luck!

---

### Post by ocusa on 2007-02-18
By coincidence I am also trying to get it to install just today on my Compaq Armada E500 (256MB RAM). 

I haven't had any luck trying to install it with the alternate version or the desktop. This could be do it with the hard disk, I think it has some bad sectors. I'll probably just use a bootdisk with fdisk to make sure. 

Just for your info

The livecd works, extremely slow and crashed (I will try it again, I was just getting too frustrated) 
The alternate version just locks up (blue screen) somwhere near the partioning, about 5 mins into the install. 

Let me know if you get it working and how, I'd appreciate it.

---

### Post by Billi on 2007-02-20
I just installed Edgy on a compaq E500, with no problems. Bear in mind that E500s came with several different speeds of processors. My system is a 700mhz pentium3 384MB of memory, (one 128 and one 256). Even with the 700mhz I have I am running Xubuntu (XFCE), I just did a standard install, then added xfce-desktop. Gnome ran fine but, I'm really used to a 3ghz, 3gig system, I also got a wireless card working, with ndiswrapper. Overall, I am pleased. Enough that I am going to slim down my windows installation even more. I read somewhere that you have to keep at least a tiny DOS system due to how the bios is updated on this computer.

If your system has a really slow processor and low memory, perhaps a mini distro like Damn Small Linux or Puppy Linux would be a better choice.

---

