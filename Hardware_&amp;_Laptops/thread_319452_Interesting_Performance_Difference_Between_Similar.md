---
title: "Interesting Performance Difference Between Similar Computers (CPU-Z)"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by altonbr on 2006-12-15
Before I convert a computer from Windows to Ubuntu, I always run the most current version of CPU-Z to record some specifications of that computer. This is so I can keep a log of people's computers incase they need to do upgrades or repairs. So firstly, I have a question about CPU-Z in Ubuntu: Is there a similar program that can do HTML outputs ("reports") and gives the same general information?

The point of this thread though is that I have two similar computers that are both running fresh install of Ubuntu 6.06 LTS (not 6.10) but they are running dramatically different.

*(See .txt files. Please note, you'll have to change them to .htm files to run. I had to change the extension due to the limitations of this forum)*


Here are the jist of the specs:
[SIZE=4]
[COLOR=Red]**_Rod_**[/COLOR][/SIZE][SIZE=4][COLOR=SeaGreen][SIZE=2] [COLOR=Black](HP Pavilion 503n, upgraded slightly)[/COLOR][/SIZE][/COLOR][/SIZE]
_**Processor** _
**Processor Type:** Intel Celeron [Williamette / 0.018nm]
**Socket: **mPGA-478
**Processor Speed:**  1700MHz (17x100MHz)
**L1 Cache:** 8KB / 12 K&#371;ops
**L2 Cache:** 128KB 
**Instruction Sets:** MMX, SSE, SSE2[U][B]

Chipset[/B][/U]
**Northbridge: **Intel i845GL rev. A1[B]
Southbridge: [/B]Intel 82801DB (ICH4) rev. 01
**Bus Speed: **400MHz

_**Memory**_
 **Type & Frequency:** DDR @ 266MHz
**Module Size:** 512MB x 2 (NOT dual channel)
**Clock Rating:** 2.5-3-3-6
  
[SIZE=4][COLOR=SeaGreen]**_Ashley_**[SIZE=2][COLOR=Black] (HP Pavilion a200n)[/COLOR][/SIZE][/COLOR][/SIZE][U][B]
Processor[/B] [/U]
**Processor Type:** Intel Celeron [Northwood / 0.013nm]
**Socket: **mPGA-478
**Processor Speed:**  2400MHz (24x100MHz)
**L1 Cache:** 8KB / 12 K&#371;ops
**L2 Cache:** 128KB 
**Instruction Sets:** MMX, SSE, SSE2[U][B]

Chipset[/B][/U]
 **Northbridge: **Intel i845GL rev. B1[B]
Southbridge: [/B]Intel 82801DB (ICH4) rev. 02
**Bus Speed: **400MHz 

_**Memory**_
  **Type & Frequency:** DDR @ 266MHz
**Module Size:** 256MB x 1
**Clock Rating:** 2-3-3-6


Now who's would you think is performing better? Ashley's has a slightly faster processor, which is made with more transistors (due to the newer transistor processing technique) but Rod's has 4x as much RAM.

Right away, everyone will probably tell me it's the RAM but from watching Corky and the System Monitor, the RAM rarley gets past 50% (128MB) full.

The installer on her computer was even noticeably slower than this other lady, Lillian's old refurbished IBM (P3 [Coppermine-T] @ 1000MHz, 16KB/16KB 256KB, 256MB of SDRAM, etc.). I was thinking that this is merely because Ashley has a cheaply made CD-ROM with next to no cache (which does not show in these specs) but even when running from the HD, it's much slower.

I checked out both HDs and I'm sure that Rod's and Ashley's both use a WD 40GB Protege (5400 RPM / 2MB Cache) using IDE. Rod though, has a 250GB secondary drive (Caviar 7200 RPM / 8MB Cache) for storage.

So do you think I should go out and buy 2x512MB PC-2700 sticks for her, or is there something fishier going on? Because I swear this lady Lillian has a faster computer than Ashley. But this could be because she doesn't have 64MB integrated GPU and has it on a seperate card... but then wouldn't that mean it should be faster than Rod's as well?

I would dive into more of the architecture specifications, but they're just so darn similar, I feel like it more has to do with dust in her computer and wear and tear on the machine than anything else. IF IT WAS DUST OR HEAT, a CPU doesn't just slow down, it cracks and stops working does it not?

Lastly, I went into "gconf-editor", went to "desktop >> gnome >> interface" and unchecked "enable_animations", but that hardly made up for any performance.

Thanks for the tips. I hope everyone will enjoy this thread as much as I will :)

---

### Post by zgornel on 2006-12-15
Celeron P4 vs P3 Coppermine ...  well, the P3 has much more power/mhz that the P4, especially if you're talking about a Celeron with 128KB cache. 256MB of ram is ok for a ubuntu installation but, the more ram you have, the better it is. In heavy multitasking, a 1GB computer will outpace for sure a 256MB one in terms of responsiveness so RAM is always an excellent investment. Check the swap usage for the Ashley machine with several mozilla, nautilus, terminals, azureus and a gimp opened :D. Check the same thing on the Rod machine. 
You could also do a series of tests like: hdparm -tT /dev/hda ; dd if=/dev/zero of=/dev/null (Ctrl+C to make it stop, read the MB/s output).

---

### Post by altonbr on 2006-12-16
Hmm, I'll make sure to try that test in the morning. What does it do? Thousands of reads and writes per second?

It's not a P3 Coppermine vs. a P4 Celeron per se... it's two P4 Celerons that basically only have RAM as being the difference between the machines. I've never seen the 256MB (Ashley) machine filled up (although, I'm not sure that's true, but that's what System Monitor tells me) and the same goes for the Rod machine. I would think that only when the RAM is filled, the CPU would then waste resources and deciding what can stay, and what needs to go (because it cached to much data). Am I way off the charts here?

Nonetheless, the obvious answer here seems to be just buy some more modules (aka: 2 512s)

---

### Post by sloggerkhan on 2006-12-16
I think the computer may try to use RAM in ratio, but that's only a guess. I installed xubuntu on a friend's comp because it only had 256 megs of RAM though it does have a newer celeron 1.2 or 1.5 ghz or so.  It almost always use RAM at about 96-132 megs, though on certain occasions it uses almost all, but I get the sense that it keeps RAM use low by taking longer to do things, and I also suspect that "free" RAM gets used as temporary cache space.  Just some guesses. But I have to guess that your issue is somehow memory related.

---

### Post by zgornel on 2006-12-16
> **altonbr said:**
> I would think that only when the RAM is filled, the CPU would then waste resources and deciding what can stay, and what needs to go (because it cached to much data). Am I way off the charts here?
 You're right but the slowdowns are more hdd related because parts of the memory pages are swapped onto the hdd to free more memory for the running programs. Eventually, if parts of the pages swapped are needed they will have to be re-brought into the ram and so on. This is a simple view of the things but when swapping is involved slowdowns are inevitable. Fortunately, the swapping mechanism in linux is far more perfomant than in Windows :D. 
The hdparm command benchmarks the read performance of the hdd. The dd command is a way to benchark the speed o the processor. It is a PIO transfer, which means that all data passes through the processor (unlike DMA where the processor is not involved). The benchmark would provide an estimate of the maximum throughput that the CPU can handle while comunicating with the southbridge. This is a speculation of mine, assuming that /dev/zero and /dev/null are considered normal devices attached to the southbridge. I might be wrong and if someone is more informed, I'm really intrested in this matter. :mrgreen:

---

### Post by altonbr on 2006-12-16
What about the Linux Benchmarking Toolkit. [http://www.ubuntuforums.org/showthread.php?t=319652](http://www.ubuntuforums.org/showthread.php?t=319652) . What is it?

[SIZE=4]**[COLOR="Red"]_Rod_[/COLOR]**[/SIZE]
> $ hdparm -tT /dev/hda ; dd if=/dev/zero of=/dev/null
/dev/hda: Permission denied
42259985+0 records in
42259985+0 records out
21637112320 bytes (22 GB) copied, 59.3232 seconds, **365 MB/s**


[SIZE=4]**[COLOR="Green"]_Ashley_[/COLOR]**[/SIZE]
> $ hdparm -tT /dev/hda ; dd if=/dev/zero of=/dev/null
/dev/hda: Permission denied
62784273+0 records in
62784272+0 records out
32145547264 bytes (32 GB) copied, 60.1385 seconds, **535 MB/s**


[SIZE=4]**[COLOR="Blue"]_My Computer_[/COLOR]**[/SIZE] (this computer should blow the others out of the water)
> $ hdparm -tT /dev/hda ; dd if=/dev/zero of=/dev/null

/dev/hda:
read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error
BLKFLSBUF failed: Permission denied
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Permission denied
46012137+0 records in
46012137+0 records out
23558214144 bytes (24 GB) copied, 53.2492 seconds, **442 MB/s**


---

### Post by zgornel on 2006-12-16
> **altonbr said:**
> What about the Linux Benchmarking Toolkit. [http://www.ubuntuforums.org/showthread.php?t=319652](http://www.ubuntuforums.org/showthread.php?t=319652) . What is it?

_[SIZE=4]**[COLOR="Red"]Rod[/COLOR]**[/SIZE]_

It's TOO old. The kit is probably a series of scripts that run several commands on the system and measure the time it took to complete them. You can do this yourself : ```
time <command>
```. The commands can be complex stuff like a *make bzImage* for a kernel or who knows what.

---

### Post by altonbr on 2006-12-16
Well what's going on with the tests there? My computer, which has much higher permorming parts, only "ranked" second place. I'm not sure about the validity of that test.

Then again, my computer has SATA drives, and hdparm is for IDE only (or so I read).

---

### Post by altonbr on 2006-12-17
Here's [COLOR="SeaGreen"]**ASHLEY**[/COLOR]'s "lspci -v", "cat /proc/meminfo" & "cat /proc/cpuinfo" output.

---

### Post by altonbr on 2006-12-17
Here's **[COLOR="Red"]ROD's[/COLOR]** "lspci -v", "cat /proc/meminfo" & "cat /proc/cpuinfo" output.

---

### Post by altonbr on 2007-07-05
I just learnt of a program called 'lshw' or Hardware Lister. So for those of you looking for a CPU-Z replacement, you can type in the terminal:
```
lshw -html > lshw.html
```
to get a .html report.

---

