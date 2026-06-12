---
title: "Ubuntu failed to work with disparate memory DIMMs"
date: 2010-02-08
forum: Hardware
---

### Post by jayelbee on 2010-02-08
I was trying out several versions of Ubuntu live CDs on a Dell GX270 (Pentuim 4 2.8 Ghz).

Over the weekend I copied a failing (windows) drive for a neighbor on the same system using 512 MB memory as 2x256 PC2700 DIMMs. Everything worked fine including installing Ubuntu to the computer and using that to copy the partition skipping five unreadable files. I returned the new drive to the neighbor with both Windows XP and Ubuntu installed it.

Today I decided to upgrade the memory using a spare 1GB PC3200 DIMM as well as one of the 256MB PC2700 DIMMs. The GX270 has two memory slots. I ran XP on the machine and did a number of things on it for a few hours without issue.

Then I wanted to backup my XP partition so booted from Clonezilla and it booted but the normally text/graphical progress screen was garbled and it eventually failed with a error that the destination drive was full which was not possible as I was copying a 20 GB partition to a drive with about 700 GB free.

I then booted from the same Ubuntu 9.10 Live CD I had used the day before and it made it to the KDE desktop but then I experienced a number of issues that were not consistent on each try:
(a) double click on install would spin the cd drive but then do nothing.
(b) Firefox experienced a crash.
(c) I would get to a screen where I was asked for a password for the Ubuntu Live CD.
(d) Various crash error messages from components.

Sorry for not being more specific but each time was a little different. At some point in the process I ran the memory test from the Live CD menu and it made it though about seven passes without error (20 minutes or so).

I finally pulled the second 256MB DIMM and then using the single 1GB DIMM installed Ubuntu from the LiveCD without issue and it is happily running and upgrading itself as I type this.

So, sorry for the long narrative, but the question is whether Linux would be more sensitive to memory configuration on this machine than was Windows XP. I plan to upgrade to a second 1 GB DIMM in the future (so Windows will run without thrashing the hard drive) but will buy an identical DIMM.

---

