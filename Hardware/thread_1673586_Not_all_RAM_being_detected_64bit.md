---
title: "Not all RAM being detected 64bit"
date: 2011-01-22
forum: Hardware
---

### Post by htmlland on 2011-01-22
Hello all,

I have just built myelf a new PC, no major issues to report of; except one strange problem. I have installed 16GB into the machine which the BIOS reads as OK as so does the memory testing tool, however on multiple terminal and GUI tools its telling me I only have 8GB of RAM. I checked lshw to find that it had been detected but ubuntu does not seem to show it in the reporting tools, is this a software problem with the memory tools or am I really running on only 8GB? I have checked every option on my BIOS and their are no options relating to reducing memory size. Below are the usual outputs that I hope will help,

Michael

-----------------------------------
**uname -a**
```

Linux mf-pc2 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
```
**cat /proc/version**
```

Linux version 2.6.32-27-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010

```
**top (extract)**
```

Mem:   8127908k total,  3038496k used,  5089412k free,   195404k buffers
Swap: 23809016k total,        0k used, 23809016k free,  1836352k cached

```
**vmstat -S M -a**
```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free  inact active   si   so    bi    bo   in   cs us sy id wa
 9  0      0   4996    766   1743    0    0     4    14   22  119 14  7 78  0
```
**free -m**
```

             total       used       free     shared    buffers     cached
Mem:          7937       2840       5097          0        190       1680
-/+ buffers/cache:        969       6967
Swap:        23250          0      23250
```
**lshw (extract)**
```

    *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: CMX4GX3M1A1333C9
             vendor: Corsair
             physical id: 0
             serial: 00000000
             slot: CHANNEL A
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: CMX4GX3M1A1333C9
             vendor: Corsair
             physical id: 1
             serial: 00000000
             slot: CHANNEL A
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: CMX4GX3M1A1333C9
             vendor: Corsair
             physical id: 2
             serial: 00000000
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: CMX4GX3M1A1333C9
             vendor: Corsair
             physical id: 3
             serial: 00000000
             slot: CHANNEL B
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
```
**Ubuntu system monitor GUI**
Attached to post.

---

### Post by dabl on 2011-01-22
Hmmm.  lshw is indeed showing 4 each 4GB DIMMs installed.

What is the motherboard make and model, and the BIOS?

Also, you might take a look at the dmidecode output, in case it reveals anything about the detection of your DIMMs.

---

### Post by psusi on 2011-01-22
Check your motherboard to see if it supports that much ram.  Also check your dmesg for the detailed memory map near the beginning.

---

### Post by Antarctica32 on 2011-01-22
My guess is your machine can't handle all of it.

---

### Post by htmlland on 2011-01-22
> **dabl said:**
> Hmmm.  lshw is indeed showing 4 each 4GB DIMMs installed.

What is the motherboard make and model, and the BIOS?

Also, you might take a look at the dmidecode output, in case it reveals anything about the detection of your DIMMs.

Checked dmidecode and it is picking up all 4 sticks in the 4 banks with the correct sizes.

My motherboard is an Intel DH55HC ([http://www.intel.com/products/desktop/motherboards/DH55HC/DH55HC-overview.htm](http://www.intel.com/products/desktop/motherboards/DH55HC/DH55HC-overview.htm)). Information on the menus in my BIOS is here [http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v14.pdf](http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v14.pdf).

> Check your motherboard to see if it supports that much ram. Also check your dmesg for the detailed memory map near the beginning.

The specs say it can handle upto 16GB. I would expect 12GB if a stick was not being read due to limitations.

Dmesg memory map (hope this makes sense to somebody :p):
```
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009ac00 (usable)
[    0.000000]  modified: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bbc4d000 (usable)
[    0.000000]  modified: 00000000bbc4d000 - 00000000bbc92000 (ACPI NVS)
[    0.000000]  modified: 00000000bbc92000 - 00000000bbd06000 (reserved)
[    0.000000]  modified: 00000000bbd06000 - 00000000bbd08000 (usable)
[    0.000000]  modified: 00000000bbd08000 - 00000000bbe0e000 (reserved)
[    0.000000]  modified: 00000000bbe0e000 - 00000000bbe0f000 (usable)
[    0.000000]  modified: 00000000bbe0f000 - 00000000bbe10000 (ACPI data)
[    0.000000]  modified: 00000000bbe10000 - 00000000bbe11000 (ACPI NVS)
[    0.000000]  modified: 00000000bbe11000 - 00000000bbe19000 (ACPI data)
[    0.000000]  modified: 00000000bbe19000 - 00000000bbe1a000 (ACPI NVS)
[    0.000000]  modified: 00000000bbe1a000 - 00000000bbe1c000 (ACPI data)
[    0.000000]  modified: 00000000bbe1c000 - 00000000bbe24000 (ACPI NVS)
[    0.000000]  modified: 00000000bbe24000 - 00000000bbe45000 (reserved)
[    0.000000]  modified: 00000000bbe45000 - 00000000bbe88000 (ACPI NVS)
[    0.000000]  modified: 00000000bbe88000 - 00000000bc000000 (usable)
[    0.000000]  modified: 00000000bc000000 - 00000000bf800000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bc000000

```

> My guess is your machine can't handle all of it.
It can handle 16GB. Linux should be able to handle lots more then that!

---

### Post by dabl on 2011-01-22
That's a very fine motherboard, and can indeed support 16GB of DDR3 memory.

Hmmmmmmmm.

Linux obtains its information about the hardware mainly from BIOS.  Is your BIOS updated?  If so, then I can't explain why the Ubuntu Linux kernel does not recognize all the memory.

You could check the performance of other 64-bit kernels, via a bootable Live CD, in case there is some limitation with Ubuntu's kernel.  Suggestions:

[[COLOR="SeaGreen"]**aptosid**[/COLOR]](http://aptosid.com/index.php?module=news)

[[COLOR="SeaGreen"]**fedora**[/COLOR]](http://fedoraproject.org/get-fedora)

[[COLOR="SeaGreen"]**Debian**[/COLOR]](http://www.debian.org/CD/)

or of course [[COLOR="SeaGreen"]**the Natty daily build**[/COLOR]](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by htmlland on 2011-01-22
> **dabl said:**
> That's a very fine motherboard, and can indeed support 16GB of DDR3 memory.

Hmmmmmmmm.

Linux obtains its information about the hardware mainly from BIOS.  Is your BIOS updated?  If so, then I can't explain why the Ubuntu Linux kernel does not recognize all the memory.

You could check the performance of other 64-bit kernels, via a bootable Live CD, in case there is some limitation with Ubuntu's kernel.  Suggestions:

[[COLOR="SeaGreen"]**aptosid**[/COLOR]](http://aptosid.com/index.php?module=news)

[[COLOR="SeaGreen"]**fedora**[/COLOR]](http://fedoraproject.org/get-fedora)

[[COLOR="SeaGreen"]**Debian**[/COLOR]](http://www.debian.org/CD/)

or of course [[COLOR="SeaGreen"]**the Natty daily build**[/COLOR]](http://cdimage.ubuntu.com/daily-live/current/)

Hmm good idea I will try another distro live CD and will double check my BIOS is updated, then I will report back.

---

### Post by psusi on 2011-01-22
It certainly appears to all be there.  What is the next screen full of dmesg after that?

---

### Post by b0b138 on 2011-01-22
Not sure if this will help or not, but I noticed that on the lshw extract that you posted, bank 0 and 1 have slot: CHANNEL A.  Bank 3 has slot: CHANNEL B. But bank 2 doesn't have that line, I would expect that it should say slot: CHANNEL B.

Have you tried reseating the sticks? Or pulled then out and tried 2 at a time to make sure you don't have a bad stick?

---

### Post by htmlland on 2011-01-23
Hello all,

@dabl I have tried the live CD for fedora and this shows the exact same result as ubuntu, this could be the fact they are similer though. A BIOS update did nothing either :(.

@psusi will repost when I get back on the machine as much as I can see that is relevent to RAM etc. from dmesg

@b0b138 I didnt even notice that! I will try pulling them one by one to see if the result in ubuntu changes, If it is a problem with the stick its a very unusual issue though as it would normally moan about it, but will still be interesting how taking 4GB out of the PC will affect the 8GB showing on ubuntu.

---

### Post by marty331 on 2012-01-31
I was having a very similar issue.  I figured out what was going on on my system.

I had recently compiled a new kernel, version 3.2.2, and for whatever reason (probably user error) it would not recognize all of my RAM.

I reinstated kernel 3.0.15 and now all my RAM is being used once again.

With your new box you are building, did you compile a custom kernel??

---

### Post by beefcakefu on 2012-06-28
Hey, I was having a similar problem on my laptop, with BIOS and `lshw` showing 4GB, while everything else showed 2GB.

Then I remembered I'd updated my `/etc/default/grub` earlier to enable screen brightness hotkeys with this command:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=Linux mem=1920mb"
```

The tutorial I followed mentioned `mem=1920mb` allowed better video performance by allocating some RAM to the onboard video card. Which I read. And promptly forgot about.

After removing that option, `update-grub` and a reboot, everything's back to normal.

For anyone else facing similar issues, `/etc/default/grub` might be a good place to look! ;)

---

