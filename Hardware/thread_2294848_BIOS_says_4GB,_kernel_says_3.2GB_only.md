---
title: "BIOS says 4GB, kernel says 3.2GB only"
date: 2015-09-13
forum: Hardware
---

### Post by NS on 2015-09-13
Resurrected  an old Dell Dimension 3100 erasing the Windows XP with Ubuntu (Xubuntu specifically, but that does not matter here).  Installed Ubuntu LTS 14.04.3 (the Xubuntu version 14.04.3) 64-bit version.  This machine has a Hyper threading, 64-bit capable Pentium 4 with 915GV Intel chipset (that is capable of max 8GB RAM). Upgraded from existing 1 GB of Kingston RAM with purchase of 2 Samsung (identical model) 2GB sticks.  I have tried all possible combinations of all 3 memory sticks, as well as testing them alone on this machine. BIOS reports 4GB or 3GB, depending on the combination of sticks i put in. All Memory sticks are good, and they run the machine individually.  

The problem is that I am seeing conflicting reports from some command line commands and  applications such as "sysinfo" or "hardinfo".  Kernel logs observed in syslog point to 3.2GB is seen by kernel - not the whole 4GB that is seen by BIOS, or other command line tools. I am suspecting that this BIOS is buggy,  and is not giving all of the address space to kernel.   Here are the links showing the conflicting reports:

[LIST=1]
[*]This is what kernel sees in syslog:  [http://paste.ubuntu.com/12404466/](http://paste.ubuntu.com/12404466/)
[*]Command line showing 4GB presence :   [http://paste.ubuntu.com/12405884/](http://paste.ubuntu.com/12405884/)
[*]Output from "hardinfo" application  :    [http://paste.ubuntu.com/12405897/](http://paste.ubuntu.com/12405897/)
[/LIST]

I have syslog output, but do not think it is necessary to post hundreds of lines here, unless someone is wanting to dive into this further.  I am aware that  this machine was originally sold to me with 2GB max RAM as published data.  But, after seeing numerous reports of others who have done 4GB, and looking into the 915GV chipset intel data, i am thinking this maybe a buggy BIOS that is not giving the final 1GB to the kernel.  Never will buy a Dell machine again.  What do you think ?

---

### Post by Bucky Ball on 2015-09-14
You have installed the 64bit release? Do you have a separate graphics card or 'onboard' graphics? Is the graphics card using some of the RAM if onboard?

Open a terminal and type 'top' and hit enter. Up the top there you should see the amount of RAM and what's being used. What does it say?

* After a sniff around, yes, this machine does have integrated graphics which would be using some of your RAM. You can probably see how much by checking in the BIOS. Looks like the machine shipped with 512mb RAM originally, so it is surprising it can take 4Gb at all. It also came with a single-core 3GHz Pentium 4 630. I would imagine that to be a 32bit processor, but I could be wrong. I have virtually the same processor (at least it is a P4 3GHz) and that is 32bit. Have you actually managed to install a 64bit release of Ubuntu on this?

You also say this: "915GV Intel chipset (that is capable of max 8GB RAM)"

? You can't add RAM to a graphics card, this one is integrated (part of the motherboard) so it uses your installed RAM. That would mean you can crank up the graphics RAM usage in the BIOS. My money's on that setting being the culprit for now. :)

---

### Post by Yellow Pasque on 2015-09-14
> The problem is that I am seeing conflicting reports from some command line commands
Well, lshw and dmidecode are going to report information about the physically installed modules, while the others are reporting the amount of addressable/usable memory, so that's expected.
> My money's on that setting being the culprit for now
~800MB being taken by an i915G?? I'll take that bet! People tend to blame IGP's for taking memory, but they usually don't take as much RAM as the user is missing.
More likely, due to to OP seeing the "magic" 3.2GB number, I'd say it's an issue with BIOS not supporting 'memory (hole) remapping' or 'memory hoisting' (or not having them enabled). So the first thing I would do is look for those options in BIOS.
[https://en.wikipedia.org/wiki/PCI_hole](https://en.wikipedia.org/wiki/PCI_hole)

> It also came with a single-core 3GHz Pentium 4 630. I would imagine that to be a 32bit processor
Cedar Mill core (65nm die-shrink of Prescott with model number 6xx) had 64-bit capability. I think some Prescotts (model number 5x1) got it too IIRC.

---

### Post by NS on 2015-09-16
Thanks for the reply  Temujin.  I have looked superficially at the syslog entries, and I am seeing only 256MB taken up by the Integrated Graphics (it is actually 915GV chipset).  You can see this also as the last line in the second link I provided above in original post.  Someone who knows where to look in syslog would be able to add up all the memory related lines, to check if  915GV  graphics processor is indeed taking up more than 256MB - very unlikely.  In fact, i posted at Intel website because the Intel whitepaper describing the technicals of 915GV ([ftp://download.intel.com/design/chipsets/applnots/30262305.pdf](ftp://download.intel.com/design/chipsets/applnots/30262305.pdf))  shows that 915GV supports ***only a maximum of 128MB*** (as Fixed + DVMT RAM allocation - see page 9 and 16).  But, i have come to the conclusion that this whitepaper is outdated, because BIOS is allocating 256MB  to graphics, as seen in the last line of second URL.

Thanks for the info on PCI hole. Even though the chipset on the motherboard (915GV memory & graphics chipset) is capable of handling unto 8GB, BIOS is pretty primitive from Dell. The wiki article you gave states that a 64-bit kernel should be able to overcome the PCI-hole using 2 techniques. I don't have any facilities in the DELL bios to change anything regarding memory.  This maybe a good situation for someone working in Ubuntu(Debian) kernel to take a look at - i don't know if there is code in Ubuntu kernel to negotiate with BIOS, for a "remapping into higher 4GB memory space"  so that drivers can live there, freeing up the memory for user.  I have confirmation from another persos with the same motherboard/system  that he sees the same PCI-hole.  

Does anyone know which lines in syslog i should refer to, so that I can figure out exactly how much memory Ubuntu kernel is getting (including Graphics, drivers etc) from BIOS ?  At this point, my only concern is to figure out  if  the 64-bit kernel is using only 3.2GB  or if it is closer to 3.5GB.  I have been able to arrive at the 3.5GB number, by adding up some other stuff I have seen in addition to the 256MB being used by the Integrated graphics processor.   If i am only getting the use of 3.2GB and the PCI-hole is wasting 1GB of RAM, i would stick in just 3GB  into this machine.  In case, the total (hidden + OS available) memory is closer to 3.5GB, then it is worth knowing the details, as a learning experience.  Do kernel gurus hang out in these forums ?  Im too lazy to go through the 1000 lines I see in the syslog, soon after a fresh boot.

---

### Post by mörgæs on 2015-09-16
Which BIOS version are you using?

---

### Post by Yellow Pasque on 2015-09-16
> Even though the chipset on the motherboard (915GV memory & graphics chipset) is capable of handling unto 8GB, BIOS is pretty primitive from Dell.
From what I've read, Intel didn't start supporting remapping until 955/965 chipsets, so I wouldn't blame Dell on this one. Even if you stuck 8GB in there and got it to work, you'd only have ~7.2 of it available to the OS.

---

### Post by NS on 2015-09-17
> **mörgæs said:**
> Which BIOS version are you using?

I am using the same BIOS that came with system (version A03). I looked into the only upgrade Dell did for this mobo (version A04), but that only addresses CPU upgrades and did not do anything about memory increase. From what i have seen on the net, someone upgraded to A04 and still had the same issue with memory.

---

### Post by NS on 2015-09-17
> **Temüjin said:**
> From what I've read, Intel didn't start supporting remapping until 955/965 chipsets, so I wouldn't blame Dell on this one. Even if you stuck 8GB in there and got it to work, you'd only have ~7.2 of it available to the OS.

Thanks Temujin.  Your reply has cleared up this issue.  I am about to submit a separate thread regarding my above query on syslog/driver related memories  under Ubuntu.

---

