---
title: "ubuntu12.04 on pandaboard"
date: 2012-09-22
forum: Hardware
---

### Post by derfan on 2012-09-22
Dear ubuntu forums,

I am using ubuntu 12.04 for ARM [1] on the pandaboard [2]. Currently running Linux version 3.2.0-1419-omap4. The pandaboard has about 900MB of RAM and I added 500MB of swap. It acts as a NAS including rsync backup, samba shares and webserver etc.

When I put it under heavy load, lets say I have an rsync backup running and access and transfer huge amounts of data from different clients at the same time then I realise some strange behaviour and somtimes the board just crashes withour an error message and i have to restart it.

The symptoms are as follows:
- I use the omap4_temp.C [3] from Mans Rullgard (hardwarebug.org) to obtain the current temperature of the omap processor. In the above mentiones scenario it stops working, meaning it runs forever displaying nothing.
- /proc/kmsg displays corrupted stuff like: wl1271: WARNING corrupted akti Xwt tts x and 861075]w17:WRIGcrutdpce nR ihsau:01
- sometimes the machine just dies without any error message...

I made the following changes already:
- increased vm.min_free_kbytes = 15000
- increased vm.swappiness = 60

Even though the system should "like" swapping when running out of memory the current memory situation looks like this:

```

# free -l -m
             total       used       free     shared    buffers     cached
Mem:           912        873         39          0         52        187
Low:           689        652         37
High:          223        221          1
-/+ buffers/cache:        633        279
Swap:          511          5        506

```Do you have any ideas on how what the problem could be and how to deal with it?

Your help would be greatly appreciated :)

Thank you and best regards,
Benjamin


[1] [http://cdimages.ubuntu.com/releases/12.04/release/ubuntu-12.04-preinstalled-server-armhf+omap4.img.gz](http://cdimages.ubuntu.com/releases/12.04/release/ubuntu-12.04-preinstalled-server-armhf+omap4.img.gz)
[2] [http://pandaboard.org/content/resources/references](http://pandaboard.org/content/resources/references)
[3] [http://hardwarebug.org/files/omap4_temp.c](http://hardwarebug.org/files/omap4_temp.c)

---

