---
title: "Files copy is very slow"
date: 2010-10-22
forum: Hardware
---

### Post by aneganov on 2010-10-22
Hi all,

When I copy my music directory with mp3 files somewhere the read speed is very slow - about 2Mb/s. 

I'm not sure what the /dev/shm is, but if its RAM, then the next command just reads files into RAM. Note the speed.

```

$ rsync --progress -av 2003\ Celldweller /dev/shm
sending incremental file list
2003 Celldweller/
2003 Celldweller/02_Switchback.mp3
    12215117 100%    2.68MB/s    0:00:04 (xfer#1, to-check=19/21)
2003 Celldweller/03_Stay With Me (Unlikely).mp3
     8954017 100%    9.91MB/s    0:00:00 (xfer#2, to-check=18/21)
2003 Celldweller/04_The Last Firstborn.mp3
    18549304 100%    4.96MB/s    0:00:03 (xfer#3, to-check=17/21)
2003 Celldweller/05_Under My Feet.mp3
     8522454 100%   11.54MB/s    0:00:00 (xfer#4, to-check=16/21)
2003 Celldweller/06_I Believe You.mp3
     8366764 100%   10.16MB/s    0:00:00 (xfer#5, to-check=15/21)
2003 Celldweller/07_Frozen.mp3
    16907746 100%    2.80MB/s    0:00:05 (xfer#6, to-check=14/21)
2003 Celldweller/08_Symbiont.mp3
    13219260 100%    2.57MB/s    0:00:04 (xfer#7, to-check=13/21)
2003 Celldweller/09_Afraid This Time.mp3
    12100190 100%    2.40MB/s    0:00:04 (xfer#8, to-check=12/21)
2003 Celldweller/10_Fade Away.mp3
    11611166 100%    2.12MB/s    0:00:05 (xfer#9, to-check=11/21)
2003 Celldweller/11_Cell #2.mp3
      961562 100%    2.27MB/s    0:00:00 (xfer#10, to-check=10/21)
2003 Celldweller/12_So Sorry To Say.mp3
    13452288 100%    2.19MB/s    0:00:05 (xfer#11, to-check=9/21)
2003 Celldweller/13_Own Little World.mp3
     8637400 100%    5.61MB/s    0:00:01 (xfer#12, to-check=8/21)
2003 Celldweller/14_Unlikely (Stay With Me).mp3
     7280092 100%    2.82MB/s    0:00:02 (xfer#13, to-check=7/21)
2003 Celldweller/15_One Good Reason.mp3
     9427341 100%    2.21MB/s    0:00:04 (xfer#14, to-check=6/21)
2003 Celldweller/16_The Stars of Orion.mp3
     7170368 100%    1.94MB/s    0:00:03 (xfer#15, to-check=5/21)
2003 Celldweller/17_Cell #3.mp3
     1398329 100%    2.02MB/s    0:00:00 (xfer#16, to-check=4/21)
2003 Celldweller/18_Welcome To The End.mp3
     9741862 100%    2.34MB/s    0:00:03 (xfer#17, to-check=3/21)
2003 Celldweller/Album Art.jpg
       29911 100%   34.98kB/s    0:00:00 (xfer#18, to-check=2/21)
2003 Celldweller/Cover.bmp
       30054 100%   35.11kB/s    0:00:00 (xfer#19, to-check=1/21)
2003 Celldweller/Front.jpg
      463622 100%  449.16kB/s    0:00:01 (xfer#20, to-check=0/21)

sent 169060973 bytes  received 396 bytes  3635728.37 bytes/sec
total size is 169038847  speedup is 1.00

```

Running the command again (after deleting copied files of course), results to rather different speeds:

```

$ rsync --progress -av 2003\ Celldweller /dev/shm
sending incremental file list
2003 Celldweller/
2003 Celldweller/02_Switchback.mp3
    12215117 100%   94.46MB/s    0:00:00 (xfer#1, to-check=19/21)
2003 Celldweller/03_Stay With Me (Unlikely).mp3
     8954017 100%   41.65MB/s    0:00:00 (xfer#2, to-check=18/21)
2003 Celldweller/04_The Last Firstborn.mp3
    18549304 100%   49.97MB/s    0:00:00 (xfer#3, to-check=17/21)
2003 Celldweller/05_Under My Feet.mp3
     8522454 100%   19.08MB/s    0:00:00 (xfer#4, to-check=16/21)
2003 Celldweller/06_I Believe You.mp3
     8366764 100%   15.65MB/s    0:00:00 (xfer#5, to-check=15/21)
2003 Celldweller/07_Frozen.mp3
    16907746 100%   24.92MB/s    0:00:00 (xfer#6, to-check=14/21)
2003 Celldweller/08_Symbiont.mp3
    13219260 100%   16.65MB/s    0:00:00 (xfer#7, to-check=13/21)
2003 Celldweller/09_Afraid This Time.mp3
    12100190 100%   13.36MB/s    0:00:00 (xfer#8, to-check=12/21)
2003 Celldweller/10_Fade Away.mp3
    11611166 100%   11.40MB/s    0:00:00 (xfer#9, to-check=11/21)
2003 Celldweller/11_Cell #2.mp3
      961562 100%  960.15kB/s    0:00:00 (xfer#10, to-check=10/21)
2003 Celldweller/12_So Sorry To Say.mp3
    13452288 100%   11.81MB/s    0:00:01 (xfer#11, to-check=9/21)
2003 Celldweller/13_Own Little World.mp3
     8637400 100%   48.74MB/s    0:00:00 (xfer#12, to-check=8/21)
2003 Celldweller/14_Unlikely (Stay With Me).mp3
     7280092 100%   29.93MB/s    0:00:00 (xfer#13, to-check=7/21)
2003 Celldweller/15_One Good Reason.mp3
     9427341 100%   28.54MB/s    0:00:00 (xfer#14, to-check=6/21)
2003 Celldweller/16_The Stars of Orion.mp3
     7170368 100%   18.04MB/s    0:00:00 (xfer#15, to-check=5/21)
2003 Celldweller/17_Cell #3.mp3
     1398329 100%    3.44MB/s    0:00:00 (xfer#16, to-check=4/21)
2003 Celldweller/18_Welcome To The End.mp3
     9741862 100%   19.73MB/s    0:00:00 (xfer#17, to-check=3/21)
2003 Celldweller/Album Art.jpg
       29911 100%   62.02kB/s    0:00:00 (xfer#18, to-check=2/21)
2003 Celldweller/Cover.bmp
       30054 100%   62.31kB/s    0:00:00 (xfer#19, to-check=1/21)
2003 Celldweller/Front.jpg
      463622 100%  955.18kB/s    0:00:00 (xfer#20, to-check=0/21)

sent 169060973 bytes  received 396 bytes  112707579.33 bytes/sec
total size is 169038847  speedup is 1.00

```

Which probably means, something was cached.

Does anybody have an idea what is going on?

---

