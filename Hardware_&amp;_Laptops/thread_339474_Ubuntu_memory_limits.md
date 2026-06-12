---
title: "Ubuntu memory limits"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by xfred on 2007-01-15
Hi guys
I'm running Dapper Drake, 32 bit version (dual processor kernel), on an asus p5n32-sli mb with a pentium d940 dual core processor.  I had 2gb of memory, but the simulations I was running (which is largely what I use the pc for) were starting to, on occasion, exceed available memory.  Hence I bought an additional 2gb to upgrade to what I presumed would be 4gb (which should be addressable by a 32 bit address bus, right?).

Bios detects 4gb no problem, mem test is fine, but for some reason ubuntu can only see 2.7gb.  Is there any way around this?  I accept that seeing the full 4gb might be a bit of an ask for practical reasons, but surely 1.3gb missing in action is a bit much?

I've messed round in the bios a bit, but the only option in there that seems to effect the amount of memory seen is the memory remap option - if I enable it then available memory drops down still further to 2gb.

Any suggestions?  Will I have to upgrade to the 64bit version?

ps: if I do have to upgrade to 64 bit, would I still be able to use the various old, 32 bit assembly code I've written for various things over the years?

---

### Post by Mike'sHardLinux on 2007-01-15
That's very curious. I have 3GB in my system, and Ubuntu(32bit) sees it all. When I had Dapper on this system, it saw the whole 3GB as well. I agree, even 32bit Ubuntu should see most of the 4GB.

What kernel are you running?
 
Before you install 64-bit, you should boot with the 64bit live cd and see how it handles your RAM.

---

### Post by xfred on 2007-01-16
My kernel version is:
Linux shadowfax 2.6.15-27-686 #1 SMP PREEMPT Fri Dec 8 18:00:07 UTC 2006 i686 GNU/Linux

---

### Post by jameskhoo on 2007-01-16
Hi all

I also face similar problem, ugraded my PC memory from 2GB to 4GB, running "top" command reveal that system  only have 3574 Mb, where the rest 500 Mb gone?

Ubuntu Version -> Drake
Kernal -> 2.6.15-27-386

Any help will me appreciated

Thanks
James Khoo

---

### Post by Mike'sHardLinux on 2007-01-17
I'm not expert enough to know the answers off the top of my head, but I have been researching this a little.

Jameskhoo, showing 3.5GB out of 4GB is very typical. Here's a link that gives one possible explanation (I know it's a windows link, but I'm pretty sure it still applies:
[http://blogs.msdn.com/oldnewthing/archive/2006/08/14/699521.aspx]("http://blogs.msdn.com/oldnewthing/archive/2006/08/14/699521.aspx")

xfred,  yours is a tough one. Makes me want to upgrade to 4GB and see if I get the same result. :mrgreen:  Anyway, I am still looking, but I found this link interesting about a similar issue in Mandriva: [http://www.linuxforums.org/forum/peripherals-hardware/68616-mandriva-does-not-recognize-all-available-memory.html]("http://www.linuxforums.org/forum/peripherals-hardware/68616-mandriva-does-not-recognize-all-available-memory.html")
I don't know if it's a kernel issue or not.

Researching this, I am amazed at how many people have similar problems where they have a system that doesn't see all of their RAM, when in fact, [it seems] it should. There's more to having a machine with lots of RAM than just plugging in the DIMMS. I wonder if this issue comes up a lot in the enterprise world where they are running servers with 64GB+ of RAM?

---

### Post by randomnumber on 2007-01-17
I do not know if is related but when I was installing Gentoo Linux I had to select options to compile into the kernel. One of the options I remember was to have large volume ram. I am sure it was called something else but you get the just of the option.

---

### Post by xfred on 2007-01-17
Thanks for the suggestions guys.

Looking around in synaptic it seems that there isn't a pre-compiled -up-4gb version available, so I guess I'll have to recompile the kernel to get these options.  It's been a while since I did this, but last time (about 2 years back on a PII pro) compiling the kernel took a bit over 2 days to complete.

About how long am I looking at for this operation on the machine I described about?  If the answer is more than a few hours it might have to wait until february.

---

### Post by RandomJoe on 2007-01-17
Heh...  It'll take you more time to go through and configure the options you want than it'll take to compile! :mrgreen: (Unless you just use a .config file from another kernel then change one or two things.)

Kernel compiles on my P4 1.8GHz laptop took maybe 20-30 minutes when I was running Slackware...  (I haven't compiled one since going to Ubuntu.)

---

### Post by xfred on 2007-02-02
Hi again

Well, I finally had time to have a go at recompiling the kernel.  There was one very hopeful looking options (64GB), but unfortunately despite much head scratching I can't get the new kernel to boot.  First off I had a message about "8254 timer not connected"... fixed by adding the noapic option.  Then I had some message about not being able to load modules.dep, which vanished after another recompile to be replaced by some message about pnp not having a proper end? or somesuch.

At that point I re-read the motherboard manual and found the following:
> - If you installed four 1GB memory modules, the system may detect less than 3GB of total memory because of address space allocation for other critical functions.  This limitation applies to windows xp 32-bit version operating system since it does not support physical address extension (PAE).

So, am I wasting my time trying to use my 4*1GB modules with 32-bit ubuntu?  Should I give up, sell my current memory and buy 2*2GB modules, or is there some way to compile the kernel that will (a) work and (b) support a reasonable fraction of my RAM?

fwiw, I was trying to compile the 2.6.19 kernel (seems to be the latest - currently I'm running 2.6.15-27-686 #1 SMP PREEMPT) following the instructions **[here]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel+compile+2.6.15")**.   My setup is:
- Asus p5n32sli deluxe motherboard
- pentium d 940 3.2GHz processor (smp)
- 4*1GB dimms
- Asus N6600 video card
- bt878 tv tuner card
- 250GB hdd (primary ide).
- dvd burner + dvd drive (secondary ide)
- 2*250GB sata hdd
- single 3.5" fdd

The motherboard has:
- A mixture of PCI and PCI-E expansion slots (no ISA, no MCA, no pmcia).
- Realtek ALC850 sound
- Nvidia nforce sli for pata and sata
- additional silicon image 3132 sata controller (currently unused)
- Marvell 88E8053 LAN controller
- Marvell 88E1115 gigabit LAN PHY
- TI 1394a firewire.

---

