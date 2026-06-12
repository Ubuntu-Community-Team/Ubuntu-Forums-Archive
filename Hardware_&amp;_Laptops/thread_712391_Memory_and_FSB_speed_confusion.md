---
title: "Memory and FSB speed confusion"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by Average Joe on 2008-03-01
I have a four year old laptop with 2x256 MB sodimm memory cards, and I am considering upgrading this memory to the maximum 2x1GB. Before doing so, I tried to figure out what kind of memory I have exactly, and what memory modules I should buy.

I have opened my laptop and took out one of the modules. It says: 256 MB DDR PC2700 CL.2.5. As I understood from [here]("http://en.wikipedia.org/wiki/DDR_SDRAM"), this means that I have so-called DDR-333 memory, that operates at a maximum clock speed of 166 MHz (because of the Double Data Rate, it can transfer a maximum of 333M data transfers per second). Also, the CAS Latency of my memory is 2.5.

So far so good. However, to have to memory operating optimally, the Front-Side Bus of my computer should be as least as fast. To figure out what my FSB speed is, I ran the commands:
```
sudo lshw -C processor
sudo dmidecode | more
```
The output of both commands say that my (external) clock speed is 400 MHz. As far as I know, this is my FSB speed (but maybe I am wrong on this).

Now comes the tricky part. The output of both the commands:
```
sudo lshw -C memory
sudo dmidecode | more
```
say that the current clock speed of my memory is actually 266 MHz. I don't see how this fits with either my FSB speed of 400 MHz or the apparent maximum clock speed of 166 MHz, as mentioned on the memory module itself.

Also, I was thinking of buying two new memory modules of 1GB DDR400 PC3200. As I understood, this memory operates at 200 MHz. Would that work well with my current FSB speed, or maybe speed things up a little? The new memory I am planning to buy has a CAS Latency of 3, which is slower than my current Latency of 2.5. Would that show down my memory significantly?

I see that this has become kind of a lengthy post. Sorry for that. I guess my questions can be summarized as:

1) What is the relation between the external clock speed of 400 MHz (= FSB speed?), the memory speed of 266 MHz, and the actual information of my memory module (PC2700)?

2) Would it be possible to upgrade to DDR400 PC3200 memory, and if so, will the memory be faster?

---

### Post by Sam Lars on 2008-03-01
Memory is just rated to certain speeds.  You can install memory that is rated faster on a slower bus, and it will just clock down to match that slower speed.
In general, it's bad to install slower memory.  It can overclock itself to match the higher bus speed, but it's not rated that fast for a reason.
There may be utilities in place to change the memory bus speed in the BIOS.

You should probably match or exceed your current memory speed.  That should be safe.
If you post more of your system specs, we may be able to answer some more of your questions.
If you have your computer manual, you can look for more information about bus speeds and what kind of memory you want to look for.

---

### Post by Yellow Pasque on 2008-03-02
Based on the evidence you've provided, your memory is probably DDR-333 being run at DDR-266 (133MHz) for the convenience of the memory divider

If your FSB is running at 400MHz and your RAM was running at 133MHz, the system would use a memory divider, in this case 3 (3*133=400). If the memory was running at its rated speed, then the divider would've been 2.5, which is not "synchronous" with the FSB and causes a loss of performance. So it appears your manufacturer chose to back off the memory speed in order to run synchronously with the FSB.

To get to the point, DDR-400 would be a very good choice, because you could run a 2:1 divider to run the memory at full speed and you would still have synchronous operation. It will offer more memory bandwidth, which should make your system faster.

---

### Post by Average Joe on 2008-03-02
Thank you for your responses. It is a bit more clear to me now. That is, until I ran Memtest86+. This test says that my FSB speed is only 99 MHz, and that my RAM is 132 MHz DDR 266. I don't see how my memory could operate faster than the FSB, so maybe this information is not entirely correct, or I am misinterpreting it. There is no information in my BIOS, nor any (memory) settings I can change there.

I have been looking for some more specific information about my laptop. There is nothing much in the manual that came with it, but some information is [here]("http://www.ciao.co.uk/Acer_TravelMate_803LMi__5792091").

Some more specs:
```
joe@ubuntu:~$ sudo lshw -C processor
  *-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) M processor 1600MHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.9.5
       slot: uFCPGA2
       size: 1600MHz
       capacity: 1600MHz
       width: 32 bits
       clock: 400MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2 cpufreq
```
```
joe@ubuntu:~$ sudo lshw -C memory
  *-firmware              
       description: BIOS
       vendor: ACER
       physical id: 0
       version: 4A14 (09/19/2003)
       size: 110KB
       capacity: 448KB
       capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 8
       slot: L1 Cache
       size: 32KB
       capacity: 32KB
       capabilities: asynchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: 9
       slot: L2 Cache
       size: 1MB
       capacity: 1MB
       capabilities: burst external write-back
  *-memory
       description: System Memory
       physical id: 10
       slot: System board or motherboard
       size: 512MB
       capacity: 1GB
     *-bank:0
          description: DIMM SRAM Synchronous 266 MHz (3.8 ns)
          physical id: 0
          slot: DIMM 0
          size: 256MB
          width: 64 bits
          clock: 266MHz (3.8ns)
     *-bank:1
          description: DIMM SRAM Synchronous 266 MHz (3.8 ns)
          physical id: 1
          slot: DIMM 1
          size: 256MB
          width: 64 bits
          clock: 266MHz (3.8ns)
```

I think what Temüjin said makes sense. That could be a good explanation why my memory operates slower than specified.

Another thing that I don't understand completely is the CAS Latency. As mentioned before, the memory itself it says: CL2.5. However, Memtest86+ says: CAS: 2-3-3-. I thought that a lower CAS latency is better (=faster), but I am not sure what I am using now. The new memory I want to buy has a CL3. Would that make my memory (much) slower, even if it matches my FSB speed better?

---

### Post by Yellow Pasque on 2008-03-02
Since the manufacturer ran the memory at a lower speed, they could tighten the timing too, so that goes along with what I hypothesized above.

The Pentium M will benefit more from the available bandwidth than tight timings, so the DDR 400 is still your best bet.

> The major issue with both of these motherboards is that they are based on the 855GME chipset. The 855GME only features AGP 4X support, but the killer is in its single-channel DDR333 memory controller. Without DDR400 support, the 855GME starves the Pentium M for bandwidth, as it is only capable of delivering 2.7GB/s of bandwidth to main memory while the Pentium M at 2.0GHz needs 3.2GB/s of bandwidth to remain most efficient
[http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=2342&p=6](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=2342&p=6)

---

### Post by Average Joe on 2008-03-02
Temüjin, I am not sure your quote is applicable for my system. I have an Intel 855PM chipset, and my processor speed is 1.6 GHz. Nevertheless, I agree that DDR400 memory is probably the best choice for me. I'll have a further look around to see what types are available (with respect to CAS latency) and at what price.

Thanks for clarifying it to me. :)

---

### Post by Average Joe on 2008-03-05
**Update:**

I have bought two memory modules of 1 GB each, type so-dimm DDR400 PC3200 CL3 and put them in my laptop.

The good news is that the 2 GB memory is recognized. The bad news is that it operates at 266 MHz, the same speed as my old memory modules (2 x 256 MB DDR266 PC2700 CL2.5). I was hoping that, with my apparent FSB speed of 400 MHz, the memory would operate faster.

I was wondering if there are some settings I can tune to speed it up. I have checked my bios, but there are hardly any settings there at all, and for the memory there is nothing to choose.

If Temüjin is right, then my memory divider is apparently still 3 (400/3 = 133 MHz). Is there a way to set this to 2 for instance, so my memory will work at 2 x 400/2 = 400 MHz?

---

### Post by Sam Lars on 2008-03-05
Just a thought... I'm not so sure about laptops, but there might be a switch or jumper on the motherboard that sets that.

---

### Post by Yellow Pasque on 2008-03-05
The correct values should be programmed into the EPD of the RAM. If the BIOS is not cooperating, check for a BIOS update or perhaps there are jumpers on your mobo as Sam suggested.

I guess it's also possible that the laptop doesn't support running 1GB sticks at DDR-400 :(

---

### Post by Average Joe on 2008-03-06
I have updated the BIOS with Winflash (luckily I am still dual booting Windows XP) and the latest BIOS version I found on the Acer website for my laptop. Apart from the new version number in the BIOS, I don't see any changes, meaning that I still cannot change memory settings.

I far as I know, there are no jumper settings on my motherboard. I will try to find some more detailed information about my motherboard before opening up my laptop (again). If there are any jumper settings, I wouldn't even now how to set them anyway.

I was hoping to be able to fix this with some software tool, like [SoftFSB]("http://www.geocities.com/enigmadeadsouls/softfsb.html") or so. I tried that under Windows, I am not sure what exact type of motherboard I have, so I had no luck there. Maybe it is simply not possible that way me for.

I'll see if I can find some more information on this. If not, I think I'll have to live with my memory the way it runs now. That is not bad. It works, and it was the cheapest I could find anyway, but it would be nice if I could get it to work just a bit faster.

---

