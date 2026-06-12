---
title: "Help on Kworld ATSC 115 TV card setup"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by maxvall on 2007-09-27
Hi.
I try to setup my Kworld ATSC 115 TV card on my Ubuntu Festy pc by folowing the next howto:
[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)
but i have problems in steps 3 & 4.1
Step 3 saids textually: *"Edit your /etc/modules file and insert an 'saa7134-dvb' right after the saa7134 entry that should already exist in the file. This will cause the module to load during boot."*, but my /etc/modules file do not have a saa7134 entry.
My /etc/modules file:
----------------------------------------------------------------------------------------
[I]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2[/I]
----------------------------------------------------------------------------------------
What to do now????? Shall i add a saa7134?????

Now then, Step 4 says textually: *"If you are using a kworld 115, you need to force proper recognition by adding the following lines to /etc/modprobe.conf"* But i dont have a /etc/modprobe.conf file!!!!!  What to do???? HELP!!!!

---

### Post by fitzman49 on 2007-09-27
> **maxvall said:**
> Hi.
I try to setup my Kworld ATSC 115 TV card on my Ubuntu Festy pc by folowing the next howto:
[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)
but i have problems in steps 3 & 4.1
Step 3 saids textually: *"Edit your /etc/modules file and insert an 'saa7134-dvb' right after the saa7134 entry that should already exist in the file. This will cause the module to load during boot."*, but my /etc/modules file do not have a saa7134 entry.
My /etc/modules file:
----------------------------------------------------------------------------------------
[I]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2[/I]
----------------------------------------------------------------------------------------
What to do now????? Shall i add a saa7134?????

Now then, Step 4 says textually: *"If you are using a kworld 115, you need to force proper recognition by adding the following lines to /etc/modprobe.conf"* But i dont have a /etc/modprobe.conf file!!!!!  What to do???? HELP!!!!

You want to create a modprobe.conf file doing this:
```
sudo gedit /etc/modprobe.conf
```

By default ubuntu does not create a modprobe.conf because it has a different file that manages modules but will search this file once it is created.  Let me know how it goes and if you happen to get sound.  I just bought the same card yesterday and I can get video but no sound.

**Edit:**You also want to add "saa7134-dvb" and "saa7134-alsa" in modprobe.conf as well so they start at boot.

---

