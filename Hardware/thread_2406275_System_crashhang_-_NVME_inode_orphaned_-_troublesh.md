---
title: "System crash/hang - NVME inode orphaned - troubleshooting tips?"
date: 2018-11-18
forum: Hardware
---

### Post by kdwoell on 2018-11-18
My Dell 9560 crashes/hangs on average once/day. Either a system message like the attached happens, or sometimes Gnome just becomes unresponsive. I've tried various things like ensuring OS is updated, Dell boot diagnostics, memory checks, temperature monitoring, etc. I'm convinced the problem is with the Samsung SSD drive. Looking for any advice and in particular any tips on how I can setup logging to run this problem down. The Samsung PM961 is not compatible with the standard disk diagnostics so looking for advice on this point also.
Edit: a little more background. This is a 2year old Dell 9560. When purchased it came with Win10. First thing I did was blow away Windows, and install Ubuntu.

OS Ubuntu 16.04 64bit
Dell XPS-15 9560
Intel® Core&#8482; i7-7700HQ CPU @ 2.80GHz × 8 

Graphics GeForce GTX 1050/PCIe/SSE2
Mem 32Gb
Drive Dell 400-APWJ, SSDR, 1TB, P34, 80S3, SAMSUNG, PM961

Output of fdisk -l:
/dev/nvme0n1: 953.9 GiB, 1024209543168 bytes, 2000409264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x86e05aaf


Device         Boot      Start        End    Sectors   Size Id Type
/dev/nvme0n1p1            2048 1934479359 1934477312 922.4G 83 Linux
/dev/nvme0n1p2      1934481406 2000408575   65927170  31.4G  5 Extended
/dev/nvme0n1p5      1934481408 2000408575   65927168  31.4G 82 Linux swap / Solaris




[ATTACH=CONFIG]281691[/ATTACH]

---

