---
title: "External dock/enclosure for internal 3.5&quot; HDDs?"
date: 2015-03-11
forum: Hardware
---

### Post by tessk2 on 2015-03-11
I have some regular desktop SATA 3.5" HDD's that I would like to be able to connect externally with an Intel NUC for quick & easy access to files. Would like to be able to pop the drives out of their current desktops, hook them up to the NUC for a few hours, then stick them back into their respective computers without issue. Any recommended hard for this? Running Xubuntu 14.04. I was looking at those USB docks that let you just drop in an internal drive. An enclosure would work as long as you can easily swap HDD's through it; I think in the past some drives have required special setup and only work with one enclosure? Or at least thats what I have heard, don't have any spares to test that theory with. Thanks.

---

### Post by efflandt on 2015-03-11
A drive caddy comes in handy if you want to connect drives temporarily. The one I got has 2 slots that work for bare SATA desktop or laptop drives and can clone drive to similar or larger drive without even needing a computer. Or it connects to a computer with USB or eSATA and has its own power supply. So you can turn it off, insert a drive, and turn it on, or swap drives the same way on the fly. The Linux partition at the far end of my drive started failing when it was becoming filled with Steam games, although the Windows partitions were not affected. So I first shrunk Win7 with its own Disk Management and cloned its partitions to a new drive using eSATA (my computer does not have USB 3.0) with the drive caddy. Then I put that drive in the computer and fresh installed Ubuntu to a then larger partition, and then used the drive caddy to copy over my home directory from the old drive. There were only a few Steam game files that were corrupted by the failing drive, but checking integrety of game files in Steam replaced those files and I was back in business.

---

### Post by tessk2 on 2015-03-11
That sounds like a good option. Do you have a link to the product you used, or the name and model number?

---

### Post by gordintoronto on 2015-03-12
I have a Vantec NexStar USB 3.0 hard drive dock which I'm happy with. It cost $40 Canadian. ($31 U.S.)

---

