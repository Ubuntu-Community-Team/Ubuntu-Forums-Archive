---
title: "Not all RAM is available"
date: 2008-08-14
forum: General Help
---

### Post by estyles on 2008-08-14
I have an Athlon 64, and had 1GB of RAM.  Last week, I went out and bought an additional 2GB, however my system (Linux Mint x386 version) is only reporting 2.5GB of RAM.  I thought there might be a problem with having more than 4GB between swap and RAM, so I reduced swap to 1GB, but it still shows only 2.5GB.  Using free gives the following output:```
estyles@bacchus ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:          2523       1037       1486          0         15        548
-/+ buffers/cache:        473       2050
Swap:         1027        187        840
```

When I run my WinXP virtual machine, it gets perilously close to using everything up.  I don't know if it matters anymore, but my RAM is not fully paired...  my machine is a little bit older, but it's not *that* old, right?  I believe it's an nForce2 chipset.

The memory section of lshw shows the following.  I can post the rest of the output if necessary.```
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM
             physical id: 3
             slot: A3
             size: 1GiB
             width: 64 bits
```

Any help or ideas?

---

### Post by Mgiacchetti on 2008-08-14
try snooping around bios??

---

### Post by estyles on 2008-08-14
BIOS reports 3145728K of RAM, which translates to 3072MB, as expected.  Other than that, not sure where to look to see if something might be disabled or enabled...  any clues?

---

### Post by tamoneya on 2008-08-14
What do you have for a graphics card.  It may be stealing your system ram and using it for graphics applications.

---

### Post by blazercist on 2008-08-14
I think the kernel counts swap as memory and it can only handle 4GB total so the swap may account for the difference.

---

### Post by az on 2008-08-14
> **blazercist said:**
> I think the kernel counts swap as memory and it can only handle 4GB total so the swap may account for the difference.

No.  The limitations on ram are on addressable ram.  Swap is not an extension of ram.

Try booting into recovery mode and running free.  In recovery mode, your graphics card is not used and you will rule out whether Xorg is allocating your system ram.

Also, post the result of 

sudo lshw -C memory

---

### Post by sayakb on 2008-08-14
If it is an architecture related issue, try this tutorial from vor: [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)
Though personally, 32-bit should be able to address 3GB of RAM.

---

### Post by estyles on 2008-08-14
> **az said:**
> Also, post the result of 

sudo lshw -C memory

```
 *-firmware              
       description: BIOS
       vendor: Phoenix Technologies, LTD
       physical id: 0
       version: 6.00 PG (12/16/2005)
       size: 128KiB
       capacity: 448KiB
       capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
  *-cache:0
       description: L1 cache
       physical id: b
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: d
       slot: External Cache
       size: 1MiB
       capacity: 1MiB
       capabilities: synchronous internal write-back
  *-cache:0
       description: L1 cache
       physical id: c
       slot: Internal Cache
       size: 128KiB
       capacity: 128KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: e
       slot: External Cache
       size: 1MiB
       capacity: 1MiB
       capabilities: synchronous internal write-back
  *-memory:0
       description: System Memory
       physical id: 1e
       slot: System board or motherboard
       size: 3GiB
     *-bank:0
          description: DIMM
          physical id: 0
          slot: A0
          size: 1GiB
          width: 64 bits
     *-bank:1
          description: DIMM [empty]
          physical id: 1
          slot: A1
          width: 64 bits
     *-bank:2
          description: DIMM
          physical id: 2
          slot: A2
          size: 1GiB
          width: 64 bits
     *-bank:3
          description: DIMM
          physical id: 3
          slot: A3
          size: 1GiB
          width: 64 bits
  *-memory:1 UNCLAIMED
       description: Memory controller
       product: CK804 Memory Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:00.0
       version: a3
       width: 32 bits
       clock: 66MHz (15.2ns)
       capabilities: ht bus_master cap_list
       configuration: latency=0
```

Doesn't look like anything more useful than what I posted before.  I will try the recovery mode thing in a few minutes.

---

### Post by az on 2008-08-14
Bank 1 is empty.  So you have the original stick of ram in bank 0 and the two new ones in bank 2 and 3.

I suggest you fiddle around.

How much ram does memtest report?

What happens if you remove the original stick and place the new sticks in bank 0 and 1?  Can you then place the original stick in bank 3?

On older computers using sdram, I used to have problems when using multiple sticks with different timings and densities.  Once, the addition of a fourth 128 Meg stick reduced the amount of memory recognized by my system to 32 megs.  Apparently, the different timing made the motherboard recognize all four sticks, but only the first 8 megs of each.  By swapping out the order in which they were placed, I was able to get the motherboard to see all the ram.

Maybe this will help.

---

### Post by Gannon8 on 2008-08-14
I think I read in my book that the kernel only addresses 2GB of memory unless you compile the kernel with a certain flag.

---

### Post by estyles on 2008-08-14
Thanks for the help attempts, guys.  I tried about half of the suggestions with no luck, and may try the other suggestions later, but I have a bigger problem now.  More on that... ;)

I booted up with a Hardy LiveCD AMD64 version and it was able to see all 3GB of RAM with free -m.  So, maybe it's a 32 bit problem?  Seems odd.  I've kinda been waiting for intrepid to come out and was planning on running the 64 bit version, assuming it comes out at the same time as x86.  There's no 64 bit version of Mint right now, so that's why I'm not using it.  Although hearing that some people are having problems with 64 bits makes me a little annoyed that I might have to use 64 bit to address less than 4GB of RAM... no big deal though.

My bigger problem right now is that Xorg appears to be hosed.  I don't know if this caused the problem, but I tried booting into recovery mode.  However I didn't have a recovery mode option in my menu.lst for 2.6.24-19 kernel that I'm currently running, so I chose the 2.6.24-16 kernel.  It then asked for a root password, which I don't have since I have the root login disabled - I thought single user mode would bypass that?  So then I told it to continue on to regular login and logged-in.  I was presented with a white-screen where I couldn't do anything and after a while, I restarted.  When I rebooted (into 2.6.24-19), suddenly Xorg was using ~40% CPU when idle and around 95% when I moved a window, causing massive lag when trying to use my system in almost any way.  I have the following messages in my /var/log/messages:```
Aug 14 22:12:15 bacchus kernel: [  159.337911] glxinfo[6782]: segfault at 00000200 eip b7fb5bad esp bfc94040 error 4
Aug 14 22:12:15 bacchus kernel: [  159.380348] glxinfo[6786]: segfault at 00000200 eip b7fa1bad esp bfddfbd0 error 4
Aug 14 22:12:15 bacchus kernel: [  159.430518] glxinfo[6792]: segfault at 00000200 eip b7f43bad esp bf86d660 error 4
Aug 14 22:12:15 bacchus kernel: [  159.539136] glxinfo[6813]: segfault at 00000200 eip b7ff3bad esp bf8c4eb0 error 4
```.

Like I said, I don't know if it's related, but it's definitely a bigger problem at this point.  I can get by using metacity instead of compiz (only because it's a lighter compositer and leaves me some headroom), although it just aleviates the problem, doesn't solve it.  I found a thread where someone else was having a similar problem in the last few days and posted there as well, but if anyone reading *this* thread has any suggestions, I'm all ears.

Anyway, thanks again, and thanks in advance if anyone is able to help with my new and improved problem!

---

