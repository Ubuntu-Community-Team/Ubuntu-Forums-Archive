---
title: "Problems with new machine"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by sbaker33 on 2006-04-30
I just built a new machine and I can't get through a Ubuntu install on it.

After typing server to specify the type of install the machine hangs before the installer is loaded.  The last command on the screen is: 
[4294670.972000] ata1: dev 0 ata, max udma/133, 195813072 sectors:

At this point the machine hangs and will go no further with the installation.  

System Specs:
MSI K8NGM-V mother board (default BIOS settings) with onboard NVIDIA graphics
AMD A64 3000+ processor
1 GB DDR 400HHz RAM
Memorex 52x IDE CD-RW
USB keyboard

I ran memtest overnight  and found no problems.  I have also installed Windows XP SP2 with no problems.  I have tried installing from multiple 5.10 CDs that have worked on other machines in the past and downloaded the AMD64 build of 5.10 last night but receive the same error with each.  (edit)I just tried a Fedora Core 5 install and it hung also, in this case at Checking dependencies for package installation ](*,) 

I am hoping this is just a BIOS change or install switch that I need to try. 

Please help!

TIA

---

### Post by jazzmuzik on 2006-04-30
That's a stange one. I know you checked the memory, but it wouldn't hurt to wiggle the RAM to see if it is fully seated. Check the HD cables too. Is the drive new or old? Sometimes you can successfully install a program but then another program will utilize the system in a more aggressively way and it will appear to be a new problem when in fact the problem was there all along. Do you have another RAM chip you could test? Is the RAM speed correctly matched to the processor? Can you swap in a different cd drive and test that?

I always ask if people are overclocking too. That can cause problems if it's running too fast.

---

### Post by sbaker33 on 2006-04-30
OK.  I reseated the memory and the HDD cables.  No change.  The HDD is new as are the cables.  No other RAM or CD ROM to test with.  The CD Rom came out of another system that I have no problems installing on it is just old and slow.  I am not overclocking unless that is a default BIOS setting (doubt it).

I tried booting with acpi=off and now I can get a clean install some of the time with the i386 install CD.  AMD64 crashes every time even with ACPI=off.  I downloaded a new ISO and still get the same result.

The hangs and error appear in random places with no pattern that I can see.  Once it was installed the system hung in the middle of and update.  

Are there any BIOS or jumper settings that I may have missed?  

Windows 2000 Server installs fine and XP seems fine as well.

---

### Post by jazzmuzik on 2006-05-01
It sounds like a hardware problem somewhere. Tough to track down. Finding it is a process of elimination in my experience. Hmm. Could be some other problem though. I'm out of suggestions for you.

---

### Post by jazzmuzik on 2006-05-01
Maybe this problem relates to yours:

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a9ec0aeedb929a42/f55c664e9fba1abb?lnk=st&q=K8NGM-V++ubuntu&rnum=1#f55c664e9fba1abb](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a9ec0aeedb929a42/f55c664e9fba1abb?lnk=st&q=K8NGM-V++ubuntu&rnum=1#f55c664e9fba1abb)

---

### Post by sbaker33 on 2006-05-04
Thanks for the advice and suggestions.  I just bit the bullet and returned the compoents and purchased an off the shelf PC.  It works fine out of the box!

---

