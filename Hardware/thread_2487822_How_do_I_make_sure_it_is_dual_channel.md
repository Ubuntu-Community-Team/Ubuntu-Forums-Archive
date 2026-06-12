---
title: "How do I make sure it is dual channel?"
date: 2023-06-15
forum: Hardware
---

### Post by bjlockie on 2023-06-15
Only 2 slots are populated.
How do I make sure it is dual channel?

```
    $ sudo dmidecode -t memory | grep -i Channel 
                Bank Locator: P0 CHANNEL A
                Bank Locator: P0 CHANNEL A
                Bank Locator: P0 CHANNEL B
                Bank Locator: P0 CHANNEL B
```

---

### Post by TheFu on 2023-06-16
Read the manual for the specific motherboard.
IME, the slots are numbered 0-3 (computer people start with 0) and with 2 sticks of RAM, I'd install them into 
0 and 2 
OR
1 and 3

If there are only 2 sticks, often the first 2 must be installed in a specific slot.  Additionally, the sticks need to be a matched set, so we can't have 8GB and 16GB sticks and expect double rate performance.  They need to come from the same package ... and it is best of there are 4 sticks that all 4 come in 1 pack (a matched set).  I've had issues trying to get (2) 2-stick sets (4 total sticks) working together at the rated performance.  They were all the exact same model, same specs.  They were 3200Mhz, but refused to boot at that speed.  Had to drop to 2900 Mhz to boot, but it wasn't stable.  Had to drop to 2666Mhz for a stable system.  

Eventually, I sold the 2 kits and replace it with a single matched set - it has been running at 3200Mhz the last 6 months, zero issues.
```
$ sudo inxi -m
Memory:
  RAM: total: 30.72 GiB used: 6.12 GiB (19.9%) 
  Array-1: capacity: 128 GiB slots: 4 EC: None 
  Device-1: DIMM_A1 size: No Module Installed 
  Device-2: DIMM_A2 size: 16 GiB speed: 3200 MT/s 
  Device-3: DIMM_B1 size: No Module Installed 
  Device-4: DIMM_B2 size: 16 GiB speed: 3200 MT/s
```
As you can see, my motherboard requires skipping slot-0 when there are just 2 sticks installed.  On my other, identical, system, RAM use is much higher **used: 25.39 GiB (82.6%) **. Normally, I share workloads between both systems, but my goal is for either 1 to handle everything critical, if needed.

---

### Post by bjlockie on 2023-06-16
I read the manual but how do I find out with a command>

```

$ sudo inxi -m
Memory:
  RAM: total: 15.53 GiB used: 3.47 GiB (22.3%)
  Array-1: capacity: 128 GiB slots: 4 EC: None
  Device-1: DIMM 0 type: no module installed
  Device-2: DIMM 1 type: DDR4 size: 8 GiB speed: 3000 MT/s
  Device-3: DIMM 0 type: no module installed
  Device-4: DIMM 1 type: DDR4 size: 8 GiB speed: 3000 MT/s
```
Would there be any benefit to 3200MT ram?

I have a laptop with 4GB on the motherboard and I put 8GB in a slot.
inxi says it has 2 slots but I only saw 1 slot so I assumed the 4GB was soldered on somewhere.
That is the one that prompted my question.
```
$ sudo inxi -m
Memory:
  RAM: total: 11.46 GiB used: 3.38 GiB (29.5%)
  Array-1: capacity: 32 GiB slots: 2 EC: None
  Device-1: ChannelA-DIMM0 type: DDR4 size: 8 GiB speed: spec: 3200 MT/s
    actual: 2667 MT/s
  Device-2: ChannelB-DIMM0 type: DDR4 size: 4 GiB speed: 2667 MT/s
```

---

### Post by TheFu on 2023-06-16
The command shown shows the speeds used by each RAM stick.  Would faster help or not?  I don't know. It depends on many things.  If you change the speeds in the BIOS, it will definitely reflect in the inxi output.

The 2nd command run shows a flaw in the setup. Unmatched RAM - both by size and speed. Big mistake. Doubt any DD will happen. For dual rate, the RAM must be matched - same model, same speed, same specs and preferably bought in the same sealed package.

Realistically, dual channel makes more difference than faster RAM.  Seriously, the differences between DDR3 and DDR4 are about 10%.  Does that really matter?  The changes at this point (since DDR2) are more about keeping RAM manufactures running so we are forced to buy new than anything else for most of us.  That's my opinion.  Read online for what the RAM pushers claim.  I ran my RAM at 2666 Mhz for over a year before replacing it with a matched set.  Have to say, I can't see any performance difference.  My systems are Ryzen, which is supposed to be more sensitive about RAM performance than Intel.

YMMV, so the only way to truly know is by testing with reproducible tests before and after each change you hope will improve performance.  OTOH, for typical daily use stuff, it just doesn't matter.

This [https://www.makeuseof.com/tag/myths-misconceptions-about-ram/](https://www.makeuseof.com/tag/myths-misconceptions-about-ram/) is a little outdated, but seems mostly true. Some of the stuff isn't completely accurate for Linux.  Beware that Linux doesn't actually validate that there is RAM when an allocation is requested by a process. Checking was making allocation calls over 5x slower, so it was decided to just return that it worked, always and leave it up to the user and system monitoring to handle over-committed RAM situations (crashing is a common "solution").  Having _some_ swap can provide the feel of the system getting slower so the user(s) can close some monster applications eating lots of RAM.  Modern browsers seem to allocate RAM and never free it.  For example, on my system right now, Brave claims to have allocated 33GB of RAM, but the system only has 32G and it is doing hundreds of other tasks, all using RAM.  In reality, Brave is using less than 1GB of RAM.
There's another process claiming to use 1.1TB of RAM.  I think it is a FIFO device for Brave and confusing RAM with throughput.
There are at least 10 other processes claiming to be using 1G-4.5G on the system. It simply isn't possible.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi       5.6Gi       5.4Gi       116Mi        19Gi        24Gi
Swap:         4.1Gi        15Mi       4.1Gi
```
shows the truth. In short, less than 6GB of RAM is being used and all those processes are lying/confused.  I like seeing RAM used for network and disk buffers.  That makes systems "feel" faster.  I also like that my swap is barely used while some RAM is available.  Swap should be one of the last things that gets involved.

On a different system, 
```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           5.7Gi       4.7Gi       546Mi        10Mi       487Mi       704Mi
Swap:          1.8Gi        15Mi       1.8Gi
```
This install is doing all that it will ever do. There's about 1GB of RAM extra. I consider that reasonable for the task. 
My goal is to have the amount of RAM needed, but not too much more.  Systems are so fast these days that with the huge performance jumps that happen every time I migrate to new hardware, it really is never worth trying to deal with 10% more performance to me.  

My last "really fast system" was a Core i5-750.  Passmark score of 2500.
I had a Ryzen 2600 a year ago. Passmark score of 13000.
Replaced that with a Ryzn 5600G for a few reasons ($120 total). Purely a CPU upgrade. Same MB. Same RAM.  Passmark score of 20000.

So, I got 50% more CPU performance for $120 and moved to a better GPU and extended the life from a 2nd-gen Ryzen to a 5th gen. Bargain!

The old i5-750 is still running. It is definitely older, draws more power than the other 2 Ryzen systems together, but for a storage server with really old storage that also needs replacement (some disks are 13 yrs old inside it), I'm just waiting for a disk failure before moving the storage to one of the Ryzens with a few open slots.  The Ryzens are about 8x faster than that Core i5 and I can feel that performance difference with server workloads.  I really don't use the Core i5 as a desktop and haven't in over 5 yrs. One of the Ryzen's isn't a desktop either, though it could be. That just isn't the purpose for the system.

Desktop RAM needs are different from server RAM needs, BTW.

---

### Post by Yellow Pasque on 2023-06-17
I don't think there's a magic command that determines channel operation. From my experience, the best way to determine dual channel is to follow the mobo manual and then maybe you can get get some confirmation on the POST screen. You may have to go into the BIOS/EFI and disable the mobo's startup logo to see diagnostic messages on the POST screen.

---

### Post by #&amp;thj^% on 2023-06-17
> **Yellow Pasque said:**
> I don't think there's a magic command that determines channel operation. From my experience, the best way to determine dual channel is to follow the mobo manual and then maybe you can get get some confirmation on the POST screen. You may have to go into the BIOS/EFI and disable the mobo's startup logo to see diagnostic messages on the POST screen.
yes there is to see if  dual channel::
```
sudo dmidecode -t 17 | awk 'BEGIN { FS=":"; OFS="\t" } /Size|Channel/ { line = (line ? line OFS : "") $2 } /^$/ { print line; line="RAM" }' | grep -iv 'no'

```
if it returns nothing it's single channel., and the same for this one:
EDIT: Below was a bad command, it is now fixed/corrected
```
sudo dmidecode -t 17

```

---

### Post by TheFu on 2023-06-17
FYI, those dmidecode commands with the grep/awk filters returned nothing on my Ryzen systems (Asus MB). They are definitely running dual channel.
Configured Memory Speed: 3200 MT/s

I looked at the dmidecode output and didn't see anything related to single vs dual channel setup.  Just the reported speeds.

---

### Post by #&amp;thj^% on 2023-06-18
Yep it's not perfect, but older users will understand the outputs. My Ryzen reports the same as yours.
```
sudo inxi -m
Memory:
  RAM: total: 7.61 GiB used: 6.65 GiB (87.4%)
  Array-1: capacity: 64 GiB slots: 2 EC: None
  Device-1: DIMM 0 type: DDR4 size: 8 GiB speed: 3200 MT/s
  Device-2: DIMM 0 type: no module installed

```
```
&#9492;&#9472;> sudo dmidecode -t 17 | awk 'BEGIN { FS=":"; OFS="\t" } /Size|Channel/ { line = (line ? line OFS : "") $2 } /^$/ { print line; line="RAM" }' | grep -iv 'yes'
[sudo] password for me: 
RAM	 8 GB	 None	 8 GB	 None	 None
RAM	 8 GB	 None	 8 GB	 None	 None


&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
second command
**EDIT: I should have checked that command before posting, this is wrong.**
[s]code]&#9492;&#9472;> sudo dmidecode -t memory | grep Channel
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
[/code][/s]

**Correction from the EDIT: Better Code below:**
```
sudo dmidecode -t 17 
```

---

### Post by Yellow Pasque on 2023-06-29
> **1fallen said:**
> yes there is to see if  dual channel::
```
sudo dmidecode -t 17 | awk 'BEGIN { FS=":"; OFS="\t" } /Size|Channel/ { line = (line ? line OFS : "") $2 } /^$/ { print line; line="RAM" }' | grep -iv 'no'

```
if it returns nothing it's single channel., and the same for this one:
EDIT: Below was a bad command, it is now fixed/corrected
```
sudo dmidecode -t 17

```

Thank you.

---

