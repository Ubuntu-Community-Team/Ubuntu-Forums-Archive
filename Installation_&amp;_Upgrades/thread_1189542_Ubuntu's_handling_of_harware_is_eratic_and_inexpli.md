---
title: "Ubuntu's handling of harware is eratic and inexplicable"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by fredj on 2009-06-16
I have Ubuntu live CDs for 7.10, 8.10 and 9.04. All of these CDs
are good copies. They all boot up on my laptop and work. In fact
I installed 9.04 on my laptop and it works perfectly.

I have a desktop machine which has what I think of as mainstream
hardware, an Intel 6850 core duo processor, a Sata II hard disk
drive set to IDE compatibility mode, an NVIDIA 7600GT video card,
4Gb of RAM, a PCI Dlink wireless card,a Samsung IDE DVD drive
and a logitech wireless keyboard and mouse. All of this runs on
an Abit IP35 motherboard. It used to run Ubuntu 7.04 with no
problems.

All of my three live CDs boot on the desktop but when I choose to
try the live system I just end up with a blank screen. I can 
install Ubuntu from an alternate CD and  I end up with a system
that allows me to log in but freezes a few minutes after log in
before I get a chance to look at the log files to try and
diagnose the problem.

So far, so bad but what I am really complaining about is this.
I have the latest Suse, Fedorra and Mandriva live CDs, all three
of these work perfectly on my desktop and I can install all three
versions and get a working system with very little effort. At
present I have Mandriva working perfectly and it is possibly the
best desktop implementation of Linux that I have seen.

I would like to install Ubuntu on all my machines but poor 
detection and handling of hardware is making this impossible.
If Suse, Fedora and Mandriva can get it right, why can't Ubuntu?

---

### Post by presence1960 on 2009-06-16
when booting the Ubuntu live CD hit F4 and choose safe graphics mode. See if that works.

---

### Post by fredj on 2009-06-17
Don't you think I've already tried that? None of the options make
any difference and none of the other Linux distributions need any
special settings. Their live disks just work, they even allow me
to get onto the Internet using ndiswrapper.

When I install them they still all work with no problems.
Mandriva not only detects my graphics card, it installs the
correct nvidia driver for it.

Tonight I tried the Mepis live disk and guess what, it works as
well, no special switches needed. I just can't find a distribution
that doesn't work, except the last three versions of ubuntu.

---

### Post by Therion on 2009-06-17
> **fredj said:**
> I just can't find a distribution that doesn't work, except the last three versions of ubuntu.
Seeing as I can't get Mepis, Sabayon or PCLOS to run on MY very typical, very mainstream hardware, I fail to see your point.

---

### Post by fredj on 2009-06-17
You say that your hardware is mainstream but you don't say what
it is, so we can have no idea if that is true. How did you check
your distribution disks were ok, please give exact details.

Sabayon and PCLOS are hardly major distributions, are they?

Were there any other versions that wouldn't install on your system?
Try all the versions, I tried then we can have a real conversation.
I would think my point is obvious to anyone and was in the title
of my original post. Please remember I am an Ubuntu user and have
been for some time. There is obviously a major bug in Ubuntu's
handling of some very ordinary hardware, a bug that is not in any
of the other major distributions. This bug wasn't present in
version 7.04 of ubuntu which installed on the same PC without
any major problems.

---

### Post by presence1960 on 2009-06-17
> **fredj said:**
> Don't you think I've already tried that? 

I only know what you post. I don't have a crystal ball. Sometimes people, myself included, overlook the obvious when there is a problem.

Anyway if Ubuntu won't work on your machine then use something that will. Each distro will not work with all hardware configurations. Sometimes we want to try to force a square peg into a round hole.

I have Ubuntu installed on my rig (self built) and my daughter's machine (a gift HP). I have installed it on many other self built machines and Dell, Gateway, HP, eMachines and Acer machines with no problems. Maybe I have been lucky, but I haven't run into a hardware configuration that Ubuntu couldn't handle. I would bet my house on the fact that there are configurations out there Ubuntu cant run on.

---

### Post by Therion on 2009-06-17
> **fredj said:**
> You say that your hardware is mainstream but you don't say what it is, so we can have no idea if that is true.
Asus P5Q motherboard, Intel E8400 C2D CPU, an nVidia 8800GTS, 4GB of Corsair DDR2 1066Mhz RAM, 2 Western Digital "Blue" caviar hard drives (SATA), Sony DRU-180 DVD-RW.

> **fredj said:**
> How did you check your distribution disks were ok, please give exact details.
I use torrents whenever possible, so the downloads are verified automatically, but beyond that how detailed can I be about using Md5 or SHA hash sums?  They either match or they don't.  I don't see you addressing your download and media burning protocols, by the way.

> **fredj said:**
> Sabayon and PCLOS are hardly major distributions, are they?
PCLOS is rated #7 on Distrowatch (dot) com, Sabayon is rated #9.  
Is being in the "Top Ten List" of Distro Watch not good enough to be considered a "major" distribution in your eye's?

> **fredj said:**
> Were there any other versions that wouldn't install on your system?
Several.  I reeeeeeally like PCLOS.  I ran it as my sole OS for many months a few years ago.  Later versions just don't like my system.  

> **fredj said:**
> Try all the versions, I tried then we can have a real conversation.
Please.  That's not even worthy of intelligent response.

> **fredj said:**
> I would think my point is obvious to anyone and was in the title of my original post. Please remember I am an Ubuntu user and have been for some time. There is obviously a major bug in Ubuntu's handling of some very ordinary hardware, a bug that is not in any of the other major distributions. This bug wasn't present in version 7.04 of ubuntu which installed on the same PC without any major problems.
Your logic is so riddled I don't know where to begin...  You're starting to really lose it here.

---

### Post by fredj on 2009-06-19
Since I an a logician I don't believe there is anything wrong
with my logic but lets forget about that.
The suggestion that I should just give up with Ubuntu and use
something else is an answer for wimps. The people who write
Ubuntu put a lot of effort into it and they want it to work on
as wide a range of hardware as possible. They don't want us to
give up on it.

I found the cause of my problem and it is as follows. In the Bios
of the Abit IP35 motherboard and maybe in other motherboards
also, there is an item called 'Onchip Sata Device->Onchip Sata
Mode'. This can be set to IDE, RAID or AHCI and by default it is
set to IDE. While all the other major live CDs and installed
systems will work no matter what the value of this item, Ubuntu
live CDs and installed systems will not work if it is set to IDE.
Of course you can just change this item but then any other
installed OS such as Windows will not longer work and will have
to be re-installed.

I have reported this as a bug since Ubuntu should be as good as
any other major distribution of Linux.

---

### Post by presence1960 on 2009-06-19
> The people who write Ubuntu put a lot of effort into it and they want it to work on as wide a range of hardware as possible.

here is my LOGIC : key words = on as wide a range of hardware as possible. Last time I checked that is not defined to include everything. 

I am glad you got it to work, but the fact remains that most distros will fail to run on every hardware configuration. That is a fact of life.

P.S. I have a Biostar TF7050-M2 mobo and my SATA mode is and always has been set to IDE mode. Have never had a problem with it. I just wanted to reboot & check my setting prior to reporting that info.

---

### Post by fredj on 2009-06-19
Well of course no distribution will work on all hardware, some
systems may lack enough memory to run the latest version, some
may have an old cpu that is just too slow. some may depend upon
hardware such as parallel ports that is now obsolete. However
there is nothing wrong with expecting that Ubuntu or any other
recent distribution will work on contemporary hardware and
nothing wrong with trying to ensure that they do.

If you have a system that is powerful enough to run the software
that you are trying to install then it is reasonable to try to 
make sure that it will install and if it doesn't let the software
writers know about it. If it doesn't install then they have
failed and you should let them know that.

If all the other major versions of Linux run on that hardware
then you should let them know that as well because that is a 
measure of their failure.

---

