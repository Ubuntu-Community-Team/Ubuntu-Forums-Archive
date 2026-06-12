---
title: "Problem loading Xubuntu after changing boot flags"
date: 2008-07-24
forum: General Help
---

### Post by PaiPimenta on 2008-07-24
I've installed Ubuntu 7.10, Gutsy Gibbon from the install DVD that came with the orange SAMS book Ubuntu 7.10 Linux Unleashed.  Originally, had trouble with screen resolution and the install screen, i couldn't make it past the time zone selection because the OK button was off screen!

So alas, I installed text only mode.  However, I got a 6% Installing Software halt, and the system didn't have X interface.  I installed a command line only system, and used aptitude to install as much software as possible, including the ubuntu desktop virtual package.

I got X windows running again and could boot directly into the GUI, but I ran into trouble when trying to adjust boot flags for my partitions.


My end goal is to have an Ubuntu server running on my desktop computer, wirelessly connected through my wireless cable router (or through ethernet cable) to my other laptops at home (two Dell Inspirons running XP Prof w/ SP2 and my iBook G4 ppc with Mac OS X 10.3.9 Panther).  That way, I could have the laptops backup files wirelessly, have a file sharing server, have laptops exchange files, etc.

I also want the desktop to be able to run XP, OS X, and perhaps Vista/DOS/etc. for educational purposes.

Right now, here is the info on my desktop:

/proc/cpuinfo reads:
processor        : 0
vendor_id        : AuthenticAMD
cpu family       : 6
model            : 6
model name       : AMD Athlon(tm) XP 1800+
stepping         : 2
cpu MHz          : 1529.433
cache size       : 256 KB
fdiv_bug         : no
hlt_bug          : no
f00f_bug         : no
coma_bug         : no
fpu              : yes
fpu_exception    : yes
cpuid level      : 1
wp               : yes
flags            : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips         : 3061.41
clflush size     : 32

/proc/meminfo reads:
MemTotal:         483240 kB
MemFree:          411336 kB
Buffers:            4376 kB
Cached:            48112 kB
SwapCached:            0 kB
Active:            10792 kB
Inactive:          43572 kB
HighTotal:             0 kB
HighFree:              0 kB
LowTotal:         483240 kB
LowFree:          411336 kB
SwapTotal:        979924 kB
SwapFree:         979924 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:          1916 kB
Mapped:             1724 kB
Slab:               6852 kB
SReclaimable:       3056 kB
SUnreclaim:         3796 kB
PageTables:           72 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
CommitLimit:     1221544 kB
Committed_AS:      37772 kB
VmallocTotal:     540664 kB
VmallocUsed:        8528 kB
VmallocChunk:     527644 kB

Here is readout from sudo fdisk -l:
Disk /deb/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024b61

   Device Boot  Start    End    Blocks  Id  System
/dev/hdb1   *       1   4255  34178256  83  Linux
/dev/hdb2        4256   4377    979965   5  Extended
/dev/hdb3        4378   7297  23454900   b  W95 FAT32
/dev/hdb5        4256   4377    979933+ 82  Linux swap / Solaris

I have a Toshiba laptop hard drive (IDE) that I want to put the data in my /dev/hdb3 W95 FAT32 partition, which is mounted to /windows onto my external hard drive which is /dev/sda.

I tried putting a boot flag on partition 3, and now I can't even boot into Xubuntu.  I pushed Esc when grub was loading to load recovery mode as root to get this info.  

It looks like X is going to load, and I see the frozen rotating film reel looking timer in the middle of the screen, plus my keyboard lock buttons flash.

Someone help me please.  I want to:
 * Fix getting into X windows
 * Mount my external hard drive, /dev/sda, and partition it so I can move my old windows data to it
 * Hopefully, move the data onto my ext. hard drive so that I can boot from the external hard drive as my old Windows XP system.


Any other info I can find and post, please let me know.

Thank you so much,

PaiPimenta:popcorn:

---

