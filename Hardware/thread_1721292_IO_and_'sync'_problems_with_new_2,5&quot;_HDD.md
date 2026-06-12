---
title: "I/O and 'sync' problems with new 2,5&quot; HDD"
date: 2011-04-04
forum: Hardware
---

### Post by ult_avatar on 2011-04-04
Hi, I have the following problem:

After I exchanged my 3,5" HDD against a 2,5" I've run into I/O performance issues. Load is high even while idling with values  at 4.0 up to 6.5 - it used to be 0.0X or maybe 0.X at times with the old disk.
Also I've found that the command 'sync' can cause kerneloops and can take ages to finish. Which is a rather big problem, as I actively use sync a lot in order to free my RAM (sync; echo 3 > /proc/sys/vm/drop_caches) because I extract/copy large files a lot. Also it causes the reboot/shutdown process to wait ages (up to hours!).

I've not come across any log entries that suggest anything. SMART short test is clean, the 2,5" HDD is new.

```

# iostat
Linux 2.6.31-14-generic (aspire)        04/04/2011      _x86_64_        (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.75    0.01    1.45   17.73    0.00   79.05

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              19.95      1700.03       347.01  240270900   49044784

```

Staring at atop for a long time, I find that the main suspect is kjournald2. But also minor read access (by a torrent seeding at ~10Kb/S) causes the HDD to be 25% busy.

Specs are:
Core 2 Quad Q8300 4x 2.50GH
8 GB RAM
2,5" Toshiba MK7559GSXP
Mainboard is Acer Aspire X3800 Series (X3812 I believe)

Filesystem is ext4 

Ubuntu 9.10 Karmic
Linux aspire 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Further Info:
I'm mainly using the Linux Box for playback via a LIRC setup(VLC, rhythmbox) but also for torrents (torrentflux-b4rt) and extracting large files. Also installed but not frequently used: mythtv, mytv and gallery3.

---

### Post by ult_avatar on 2011-04-09
bump

---

