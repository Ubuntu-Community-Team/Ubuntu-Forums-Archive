---
title: "Failing System?"
date: 2012-03-02
forum: Hardware
---

### Post by bulazeem on 2012-03-02
I know that this area of the forum is for "problems with hardware & laptops not being detected or supported during or after install" but I don't know where else to post this thread.  I've also posted on a hardware forum (tom's) and haven't gotten a reply yet.  Sorry if this is in the wrong area.

My computer runs fine in Windows XP for a time range between 1 min to 2 hours. It starts having problems for what appears to be no specific reason at a random time under low or high stress conditions. System monitor didn't shows CPU load to be 100% on the performance page but no processes seem to be utilizing the CPU at all. In an advance system monitor that I downloaded, the process that's hogging the CPU load seems to be "interrupts". It states hardware or DPCs if i recall correctly. I then tried a lighter OS to see if it would help and it seemed to make a huge difference. I installed Ubuntu 10.04 and everything seemed to run fine with minor freezes occurring for 1-3 sec at random intervals but not exceeding maybe 8 times per hour (sometimes a couple in a row, sometimes rather spaced). However, it would never spike to 100% and sit there making everything else unable to run like it did in WinXP. The only problem with Ubuntu though is that it seems to be unable to boot after approximately 10 reboots or so, without changing configurations or programs except for after the initial boot up after install. I've put it back on my system twice since then only for the same thing. I've now given up and just run my computer from a Ubuntu Live CD. So the functionality of this PC is quite low for that reason. Since January, I've put in two hard drives because I thought they might be to blame being unable to retain data or something. This is a very annoying issue and maybe my PC is just getting too old to keep going anymore, any help would be appreciated. Thanks!

System:
Athlon 64 3400+ (seems to run at about 51C when running programs)
LanParty UT NF3 250GB
GeForce 7600GT
Seagate Barracuda 500GB SATA drive with jumpers set to limit transfer rate to 1.5Gb/s
2 GB DDR400 Ram (I let memtest run 3 full sequences with 3 passes 0 fails)
3 disc drives
Not exactly sure what PSU but I did unplug 2 of the 3 drives (need one for live CD booting) and unplugged a PCI fan card that's near the 7600 to try to reduce load and it didn't seem to make any difference.

Link to mobo manual if anyone needs any specifics on it img.dfi.com/Upload/Manual/CM/lp%20ut%20nf3%20250gb%2081000414-r.pdf

---

### Post by gdea73 on 2012-03-02
That seems a bit strange... so you're describing random system freezes, most/all of which the system eventually comes out of, but the CPU usage spikes to 100% on XP. I haven't ever seen faulty hardware cause a high CPU load directly, though I'm guessing there is some sort of hardware problem causing the temporary lock-ups.

I would be willing to bet it is maybe the RAM or power supply. Basically, run whatever tests you can to rule things out. Boot to an Ubuntu LiveCD or an Ultimate Boot CD and run memtest86+. Try to leave the computer running until you get at least five passes. If you get errors, note which part of the memtest causes them. You'd likely need to replace RAM in that case, after trying with each individual stick separately.

If the RAM is okay then it might be a power supply over/under voltage on the 12V line to the motherboard, causing some weirdness. I can't say for sure, but I know faulty power supplies can cause really strange problems sometimes. Perhaps invest in a multimeter, or otherwise a power supply tester (the RTK-PST is somewhat inexpensive on Newegg, I have one and it seems to work fine). Multimeters would generally be more accurate but also testing the 12V line with a multimeter requires a lot more technical skill, time, etc.

I don't know, I recommend you run memtest86+ with the current configuration and let us know what happens. :)

---

### Post by bulazeem on 2012-03-05
Ok so I ran the memtest 6 times and it passed all 6 times.  I don't have any extra money to go and buy something to test my PSU at the moment, sadly, but at least it seems like I've completely eliminated the memory from the problem.  For now, I'll have to keep running 10.04 from a CD (good news is that it runs smoothly :D  ), and I'll let you guys know the results of PSU tests when I can get around to it.  Thank you gdea73 for your help thus far.

---

