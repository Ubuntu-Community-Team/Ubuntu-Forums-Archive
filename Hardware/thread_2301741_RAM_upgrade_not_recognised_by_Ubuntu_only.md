---
title: "RAM upgrade not recognised by Ubuntu only"
date: 2015-11-04
forum: Hardware
---

### Post by as_in_sherlock on 2015-11-04
I have a Dell Latitude E6530 which came with 8Gb of RAM (2x 4Gb).
I have just upgraded to 16Gb with the CT4470630 upgrade kit (2x 8Gb) from Crucial which is guaranteed compatible with my laptop:
[http://uk.crucial.com/gbr/en/latitude-e6530/CT4470630](http://uk.crucial.com/gbr/en/latitude-e6530/CT4470630)

I have updated to the latest A17 BIOS available for my laptop:
[http://www.dell.com/support/home/us/en/04/product-support/product/latitude-e6530/drivers/advanced](http://www.dell.com/support/home/us/en/04/product-support/product/latitude-e6530/drivers/advanced)

The RAM is recognised correctly as 16Gb by the BIOS and my dual-boot Windows 7 installation, as well as memtest86+
However it is **not** recognised by Ubuntu 15.10 (64-bit) which reports only 7.2Gb in the Details app.

free -m
             total       used       free     shared    buffers     cached
Mem:          7411       6543        867        639        261       2803

Why does Ubuntu not see it when other OSes do?  How can I fix this? All help appreciated :)

---

### Post by weatherman2 on 2015-11-05
Try booting the live USB and see what is reported.

What's the content of the file /proc/meminfo ?

---

### Post by as_in_sherlock on 2015-11-05
Thanks for the advice - will try booting off an Ubuntu live CD tomorrow.  Have a few old live CDs of various OSes lying around but nothing recent so I doubt they'd be 64 bit but can try them too and report back.

cat /proc/meminfo 
MemTotal:        7589252 kB
MemFree:          115220 kB
MemAvailable:    2815660 kB
Buffers:          245096 kB
Cached:          3014560 kB
SwapCached:         5680 kB
Active:          4674200 kB
Inactive:        2286068 kB
Active(anon):    3299332 kB
Inactive(anon):  1138368 kB
Active(file):    1374868 kB
Inactive(file):  1147700 kB
Unevictable:          92 kB
Mlocked:              92 kB
SwapTotal:       8257532 kB
SwapFree:        8126896 kB
Dirty:              9796 kB
Writeback:             0 kB
AnonPages:       3696492 kB
Mapped:           883060 kB
Shmem:            736864 kB
Slab:             348640 kB
SReclaimable:     218864 kB
SUnreclaim:       129776 kB
KernelStack:       12848 kB
PageTables:        81836 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    12052156 kB
Committed_AS:   12050736 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      361816 kB
VmallocChunk:   34358947836 kB
HardwareCorrupted:     0 kB
AnonHugePages:    833536 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      304556 kB
DirectMap2M:     7489536 kB

---

### Post by SuperFreak on 2015-11-05
I don't think 32 Bit Ubuntu OS will recognize anything above 4GB of RAMMemory

Edit: May be wrong about that:
A 32-bit computer has a word size of 32 bits, this limits the memory theoretically to 4GB. This barrier has been extended through the use of 'Physical Address Extension' (or PAE) which increases the limit to 64GB although the memory access above 4GB will be slightly slower.

A 64-bit computer will be able to address up to 16.8 million TB (16 exabytes) although constraints are in place that limit this to around 1TB.
[https://help.ubuntu.com/community/32bit_and_64bit]("https://help.ubuntu.com/community/32bit_and_64bit")

---

### Post by as_in_sherlock on 2015-11-06
Fantastic!  I have an Ubuntu 13.10 64 bit live CD/DVD and booting off that reports the full 16gb RAM - see below.
So, the question is, how do I get my current install to recognise it?  Do I need to wipe the existing installation and do a full reinstall?
Looking back, I probably installed the laptop originally from this Ubuntu 13.10 64 bit live CD/DVD 2 years ago  but I guess it might be different if I downloaded the latest 15.10 image and did a fresh install from that?
I'd rather not have to wipe everything and start from scratch again though....

[FONT=arial]ubuntu@ubuntu:~$ free -m[/FONT]
[FONT=arial]             total       used       free     shared    buffers     cached[/FONT]
[FONT=arial]Mem:         15954       1592      14362          0        146        893[/FONT]
[FONT=arial]-/+ buffers/cache:        552      15402[/FONT]
[FONT=arial]Swap:            0          0          0[/FONT]


[FONT=arial]ubuntu@ubuntu:~$ cat /proc/meminfo [/FONT]
[FONT=arial]MemTotal:       16337852 kB[/FONT]
[FONT=arial]MemFree:        14208172 kB[/FONT]
[FONT=arial]Buffers:          182204 kB[/FONT]
[FONT=arial]Cached:          1094244 kB[/FONT]
[FONT=arial]SwapCached:            0 kB[/FONT]
[FONT=arial]Active:           952300 kB[/FONT]
[FONT=arial]Inactive:         944300 kB[/FONT]
[FONT=arial]Active(anon):     668924 kB[/FONT]
[FONT=arial]Inactive(anon):   352368 kB[/FONT]
[FONT=arial]Active(file):     283376 kB[/FONT]
[FONT=arial]Inactive(file):   591932 kB[/FONT]
[FONT=arial]Unevictable:           0 kB[/FONT]
[FONT=arial]Mlocked:               0 kB[/FONT]
[FONT=arial]SwapTotal:             0 kB[/FONT]
[FONT=arial]SwapFree:              0 kB[/FONT]
[FONT=arial]Dirty:                 0 kB[/FONT]
[FONT=arial]Writeback:             0 kB[/FONT]
[FONT=arial]AnonPages:        620172 kB[/FONT]
[FONT=arial]Mapped:           195396 kB[/FONT]
[FONT=arial]Shmem:            401140 kB[/FONT]
[FONT=arial]Slab:              82868 kB[/FONT]
[FONT=arial]SReclaimable:      55704 kB[/FONT]
[FONT=arial]SUnreclaim:        27164 kB[/FONT]
[FONT=arial]KernelStack:        3416 kB[/FONT]
[FONT=arial]PageTables:        27128 kB[/FONT]
[FONT=arial]NFS_Unstable:          0 kB[/FONT]
[FONT=arial]Bounce:                0 kB[/FONT]
[FONT=arial]WritebackTmp:          0 kB[/FONT]
[FONT=arial]CommitLimit:     8168924 kB[/FONT]
[FONT=arial]Committed_AS:    3638188 kB[/FONT]
[FONT=arial]VmallocTotal:   34359738367 kB[/FONT]
[FONT=arial]VmallocUsed:      372016 kB[/FONT]
[FONT=arial]VmallocChunk:   34359363160 kB[/FONT]
[FONT=arial]HardwareCorrupted:     0 kB[/FONT]
[FONT=arial]AnonHugePages:         0 kB[/FONT]
[FONT=arial]HugePages_Total:       0[/FONT]
[FONT=arial]HugePages_Free:        0[/FONT]
[FONT=arial]HugePages_Rsvd:        0[/FONT]
[FONT=arial]HugePages_Surp:        0[/FONT]
[FONT=arial]Hugepagesize:       2048 kB[/FONT]
[FONT=arial]DirectMap4k:       93612 kB[/FONT]
[FONT=arial]DirectMap2M:    16586752 kB[/FONT]

---

### Post by weatherman2 on 2015-11-06
I'm fairly sure you can find a way to see all the RAM without re-installing, though a solution eludes me at the moment.  However, 15.10 isn't the version I would choose to install myself if I were starting over, just because it is supported only a few months, but I assume you know that.  I would be sticking with 14.04 LTS so I wouldn't have to upgrade again til 2019.

I've never had this kind of problem adding RAM to an existing Ubuntu installation - it's always just recognized the new RAM automatically.

I suppose it might be a useful exercise to boot 15.10 live from a USB just to make sure it too sees the full amount of RAM, to verify that indeed there's just something messed up with your particular installation and not some problem with 15.10 seeing the new RAM.  There is a much newer kernel in 15.10 than in 13.10 - I suppose that could make a difference.

---

### Post by matt_symes on 2015-11-06
Hi

Can we look in dmesg and see what it is saying.

Reboot your machine and login.

Then please post the output of these commands.

```
dmesg | egrep "(e820|[Mm]emory)"
```

```
cat /proc/cmdline
```

```
cat /proc/mtrr
```

Kind regards

---

### Post by as_in_sherlock on 2015-11-07
Thank you *so* much.
cat /proc/cmdline revealed that I had mem=8192m set in my grub boot parameters..  I can't remember why for the life of me, but presumably I added it at some point in the distant past for some reason...
Not something I ever thought to check - sorry about that.
All fixed now, again, huge thanks :)

---

### Post by matt_symes on 2015-11-08
Hi

> **as_in_sherlock said:**
> Thank you *so* much.
cat /proc/cmdline revealed that I had mem=8192m set in my grub boot parameters..  I can't remember why for the life of me, but presumably I added it at some point in the distant past for some reason...
Not something I ever thought to check - sorry about that.
All fixed now, again, huge thanks :)

You're welcome.

I'll mark this thread as [solved] for you.

Kind regards

---

