---
title: "Ram utilization and other problems..."
date: 2012-03-05
forum: Hardware
---

### Post by cdednam on 2012-03-05
Hi everyone,

I have recently installed Ubuntu 9.10(I know its old) but I'm still waiting for my ADSL line so I can upgrade to the newest version. But in the meantime I have an issue with the ammount of RAM my machine picks up.

I have 8GB of ram installed but my machine only picks up 2.9GB, how can I get the system to increase the usage to its full potential?

And I would like to totally switch over to Ubuntu so I would like to find out if anyone can tell me how to save my Windows Outlook mail to a backup so that I can import it to whatever mail program is best suited, be it Mutt or Evolution, would preferr Mutt.

Help would be much appreciated. 

Thank you,

Cornel

---

### Post by sanderj on 2012-03-05
You're probably using the 32-bit version of Ubuntu, right? A 32-bit OS will only see more than 3GB RAM if you use the PAE kernel. See [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) to install the PAE-kernel on your 32-bit Ubuntu.

Oh, and your hardware (BIOS etc) also needs to support 3+GB. I have a script to check that: [http://www.appelboor.com/dump/check-my-hardware.py](http://www.appelboor.com/dump/check-my-hardware.py) . Run it as root.

As you have 8GB RAM, I think you have modern hardware, and I don't expect any problems there.

Example output from my script:


```
$ sudo python check-my-hardware.py 

check-my-hardware.py - version: SJ 2012-03-05
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 3890 MB as usable
Memory seen by OS 3760 MB
BIOS version 06/21/2010
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 206 MB
Memory difference between BIOS offering and memory seen by OS 130 MB
Memory difference between DIMM hardware and memory seen by OS 336 MB

ADVICE:
Nothong unusual found, so no advice for your setup

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: SODIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 2GiB
          description: SODIMM DDR3 Synchronous 667 MHz (1.5 ns)
          size: 2GiB
          description: SODIMM DDR3 Synchronous [empty]
          description: SODIMM DDR3 Synchronous [empty]

Finished
```

---

### Post by cdednam on 2012-03-16
Thank you for the help sanderj,

I used the:

[FONT=Courier New] linux:~$ sudo aptitude install linux-generic-pae linux-headers-generic-pae[/FONT]

 and my machine gave me the folwing:

[FONT=Courier New]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done[/FONT]

Checked it and voila...

[FONT=Courier New]root@cornel-linux:~# free -m
             total       used       free     shared    buffers     cached
Mem:          7967        753       7214          0         64        381
-/+ buffers/cache:        307       7660
Swap:            0          0          0[/FONT]

I appreciate the help a lot.

---

