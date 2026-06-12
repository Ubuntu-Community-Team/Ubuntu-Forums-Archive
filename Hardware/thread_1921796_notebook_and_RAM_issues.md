---
title: "notebook and RAM issues"
date: 2012-02-07
forum: Hardware
---

### Post by spezticle on 2012-02-07
EDIT:
strange. MEMTEST86+ didn't detect errors the first time. ran it again and i'm getting all kinds of failing addresses.
I'm leaving the rest of my post intact for reference, but primarily, my issues now are solely identifying which ram sticks belong to the failing addresses.

> if I understand correctly, if ram passes a memtest check, that would eliminate the possibility of a faulty ram stick? 

First off, this is sort of Ubuntu relevant. I've opened up a whole lot of problems for myself and i have to start somewhere. I keep trying to install ubuntu and it keeps failing throughout the process telling me my disk failed a CRC check. There might be something wrong with my optical drive seeing as some of these disks im trying I just burned at 4x and i can't get it to boot properly from USB. I've tried 11.04, 11.10 and mint 11 all x64.


the hardware:
I have an asus notebook n53SV. It came stock with 6GB 1333 SODIMM DDR3. 
a 4GB and a 2GB, leaving 2 more ram slots open.

I recently purchased 16GB in 4x4GB chips to max out my RAM capacity.
Upon installation my windows system BSOD. Firefox was also crashing strangely.
So i started to test the ram. I tried testing my system with only one of the newly installed ram chips installed. Did this for each of the 4 of them.

Then I installed them in pairs and cycled through until i tested the pairs in all combination.
Everything was fine. no BSOD. Only when there is all 16gb installed.

This process of testing was lengthy and annoying as you can imagine. I ran benchmarks on my ram to test them.

I haven't had a chance to do any ram benchmarks or tests in Linux yet, i'm working on trying to get a version of linux installed on the computer.

This is my first notebook pc, so i'm pretty n00b to issues that come along with compatibility.

---

### Post by jerrrys on 2012-02-08
And your running 4 core?

DDR3  1333 MHz SDRAM, 4 x SO-DIMM socket for expansion up to 16 G SDRAM (Quad  Core), 2 x SO-DIMM socket for expansion up to 8 G SDRAM (Dual Core) 

[http://www.asus.com/Notebooks/Multimedia_Entertainment/N53SV/](http://www.asus.com/Notebooks/Multimedia_Entertainment/N53SV/)

---

### Post by pixiq on 2012-02-08
I guess you can run the test so that you systematically have sticks inserted or not, so that you can exclude the bad stick(s). Or if it is a socket on the motherboard that is bad. But there is a small part of the first stick, that is used to store the program memtest (which will not be tested).

I did it once (several years ago), and actually I did not succeed in tracking down a bad stick, and needed help. So take your time and work systematically! Take notes ... (and yes, it takes time)

---

### Post by spezticle on 2012-02-08
> **jerrrys said:**
> And your running 4 core?

DDR3  1333 MHz SDRAM, 4 x SO-DIMM socket for expansion up to 16 G SDRAM (Quad  Core), 2 x SO-DIMM socket for expansion up to 8 G SDRAM (Dual Core) 

[http://www.asus.com/Notebooks/Multimedia_Entertainment/N53SV/](http://www.asus.com/Notebooks/Multimedia_Entertainment/N53SV/)
yeah, it's the quadcore. 
i'm waiting on replacement chips that should arrive tomorrow. next i have to work on getting ubuntu to boot. only boots to a black screen. pretty sure its a graphics driver issue, but not sure yet. i'll look into that more in the morning

---

### Post by jerrrys on 2012-02-09
Optimus

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NVIDIA%C2%AE+GeForce%C2%AE+GT+540M&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NVIDIA%C2%AE+GeForce%C2%AE+GT+540M&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Optimus&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Optimus&sa=Search&cof=FORID:9)

---

