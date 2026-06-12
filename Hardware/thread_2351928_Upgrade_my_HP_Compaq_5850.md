---
title: "Upgrade my HP Compaq 5850"
date: 2017-02-07
forum: Hardware
---

### Post by lammert-nijhof on 2017-02-07
I like to optimize the machine taking into account price/performance issues. The HP 5830 has 4 GB of RAM and a 3 core AMD Phenom processor at 2.3 MHz. The motherboard is displayed as HP 3029h. 

As an example of price performance I considered replacing my 80 GB system disk with a SSD of 64 GB. I checked the speeds of both disk the 80 GB and my 500 GB data disk. Realizing that the big disk was twice as fast. After some gparting and editing I moved my Ubuntu 16.04 OS to the big disk and it halved my boot time to 42 seconds. If I include typing the password and loading Conky, Skype, Whatsie and Thunderbird it takes 1 min and 20 seconds. The system is also more responsive during normal use. I am happy with that aspect now.

I don't have memory problems and after I enabled zswap I could load two VMs (XP and 2000) and all apps I use without a problem. I don't have any cpu speed problems, except when I start using Screen Recording or Video Editing. To speed those things up I could do 3 things:
[LIST=1]
[*]Change memory from 667 MHz to 800 Mhz for approx $30 and/or
[*]Change my cpu to a Phenom X4 9850 at 2.5 MHz for approx. $30 and/or
[*]Change the 80 GB disk to a SSD for again approx. $30.
[/LIST]
I'm basically happy with my boot time and responsiveness and I'm happy with my memory size. All cpu cores run at 95% during the video processing. In theory I could calculate a speed increase of 4/3 x 2.5/2.3 x 800/667 = 1.74 so a 74% improvement in performance. The SSD would not bring any improvement to the video processing, because it is completely CPU bound. The memory upgrade could bring  in theory 19% and the cpu upgrade 45%.
The question is: How much would these improvements reduce my video generation time in practice?

---

### Post by lammert-nijhof on 2017-02-07
OK I think I found the answer my current processor has passmark = 1697, while the one I like has 2895. According to the specialists this is a real measure for cpu comparison, so the new processor would bring 2895/1697 = 1.71 say a improvement of cpu speed of 70% with the memory upgrade it would bring a doubling of my processor speed. Correct?

I did detect another potential issue, I use integrated graphics with a 256 MB display buffer, that will use some of my memory bandwidth. That memory bandwidth is shared between CPU and Integrated GPU, that I could avoid, if I used a simple video card with its own memory, true? 
My theoretical memory bandwidths is: 667.000.000 x 2 (DDR2) x 64 x 2 channels = 170 Gbits/sec. My Integrated GPU would use how much?

---

### Post by Bucky Ball on 2017-02-07
Well, one is 2.3Mhz and the other is 2.5, so not sure how that equates to a 70% increase in CPU speed ... doesn't look that huge a diff to me, but that is hard to confirm until you give the exact model of the CPU you have at present, which you haven't as yet. ;)

---

### Post by lammert-nijhof on 2017-02-08
The current processor is AMD Phenom X3 8600B at 2.3 GHz and I was thinking now about a Phenom X4 9850B of 2.5 GHz. If you look at the performance tests of Passmark, they measured a 3160 vs 1697 passmarks of CPU performance on their benchmark runs of the 9850B and the 8600B. The main physical difference will be, that that the 9850B has one core more and supports 1066 MHz DDR2 memory instead of 800 MHz. My HP 5850 manual also mentions 1066 MHz as a supported speed.  For my PC it would mean say: 3160/1697=1.86 with a correction because of the memory speed difference of the real PC 667 MHz and the measurement on 800 Mhz. The final improvement would be 800/667*1.86 = 2.2. Let say a doubling of the CPU speed of my current PC would be realistic if I replace CPU and memory. 

I also looked now at upgrading the BIOS and the new version of the BIOS, which I downloaded. That new BIOS also supports the AMD Phenom II C-2 Step Series Processors. Which means a 3.0 GHz processor like the Phenom II X4 B95 with the DDR2 of 1066 MHz. Those CPUs with AM3 socket will be usable in AM2+ sockets too. That would be an even larger improvement from 1697 passmarks to 3826. However that will have been measured with DDR3 1333 MHz memory. Let's assume a correction for memory speed as 1066/1333*3826=3060. Which is too low so let's half the difference 3443. This option seems not very much better, more expensive and a little bit more risky, since these range of AM3 CPUs were not on the market during the period the motherboard has been designed. 

My remaining question is:
- How many memory cycles or percentage memory bandwidth is the Radeon 3100 integrated graphics stealing from the CPU in a normal non gaming environment?

My VGA display uses 1680 x 1050 pixels at 60 fps (xrandr) and 24 bits colors (max vsync 75 Hz, hsync 83 Hz). On YouTube during quiet moments on the net, it supports 1080p full screen. It is an old, good quality Fujutsi/Siemens LW22 22" LCD with only a VGA plug and an audio-in plug (with two lousy 1 Watt speakers).

---

### Post by lammert-nijhof on 2017-02-08
Again... My memory bandwidth will increase from 667 x 64 x 2 x 2 = 171 GBits/sec to 1033 x 64 x 2 x 2 = 273 GBit/sec. The video frame buffer will be 1680 x 1050 x 3 = 5.2 Mbytes. Suppose GPU uses double buffering. For the display the buffer is refreshed 75 x second, which results in 5.2 x 8 x 75 = 3.1. Gbits/s. Suppose you need for the second frame buffer and the two other buffers also the same throughput of 3.1 GB/s each, then the total throughput will be 12.4 GB/s. It would take 7.2% now and 4.6% of the theoretical maximum memory throughput. No problem I think/hope.

My conclusion buy 2 x 2 GB DDR2 1066 MHz and a AMD Phenom X4 9850B [COLOR=#000000]processor. [/COLOR]

---

