---
title: "Ubuntu 9.04 with ext4 copy/move files cause system to respond very slow"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by gen.fengle on 2009-05-07
Yesterday I installed 9.04 (final release) x86_64 with ext4 on my new harddisk. Everything seems fine except that when I copy or move large amount of files(more than several GB) the system becomes [COLOR="Red"]very very slow[/COLOR] that I can't even run other app smoothly. 
The copy rate is quite ok -- 65~78MB/s when copy between harddisks.

I [COLOR="Red"]didn't[/COLOR] had this issue on my old harddisk with 9.04 RC installed(also 64bit with ext4). And in Windows vista it is [COLOR="Red"]also[/COLOR] ok. 

Does anyone experience the similar issue??:(

---

### Post by gen.fengle on 2009-05-08
nobody???

---

### Post by Sef on 2009-05-08
Please wait 24 hours before bumping your thread.

As for your problem, please list your hardware specs.

---

### Post by gen.fengle on 2009-05-08
My hardware spec is in my signature...

---

### Post by sroland81 on 2009-06-25
Me too!, i have a new laptop HP 6735s business and installed Jaunty fresh amd64 with Ext4 filesystem. Noticed that when moving files (sveral GB to an external usb harddrive) the system is unusable. dragging windows very slow and sereval seconds to popup menus to appear... cube rotation with 1 or 2 fps... is this issue due to 3D drive guard of my notebook HHD?? firefox turns black and white, apps take several tenths seconds to respond... back in time i used to perform an ext3 tune-up by switching realtime to noatime and that worked fine... is this possible with ext4?

thanks,

---

### Post by moster on 2009-06-25
You are not alone. You can enable AHCI in BIOS, that will change you current IO driver.... But be carefull look at this thread
[http://ubuntuforums.org/showthread.php?t=1162132]("http://ubuntuforums.org/showthread.php?t=1162132")

Look at your MBO manual for different way of operating with disk. Sometimes it is called native sata, sometimes AHCI...

check  for DMA settings too. Maybe it is not ON for some reason
```
dmesg | grep -i dma
```

---

### Post by sroland81 on 2009-06-25
I switched the bios... it was configured in AHCI and i switched to IDE and everything seems all right... i'm now performing 8GB files copy from external HDD and system is fine and responsive... compiz is working full throttle as the files are being copied...

thank you very much!

anyway what is the difference with AHCI and IDE modes?
which is better?

---

### Post by gen.fengle on 2009-06-26
glad to see this dead thread going alive again..
It will be interesting to test. I remember(i don't have access to my desktop now) that in my bios the ahci is enabled all the time. 

btw, when I use 9.04, no matter it is ext4 or ext3 or mixed, it has this issue of low/no response from os when copying files. So it seems to make perfect sense that the driver itself has some problems. 

thx for the indications

---

### Post by moster on 2009-06-26
> **sroland81 said:**
> I switched the bios... it was configured in AHCI and i switched to IDE and everything seems all right... i'm now performing 8GB files copy from external HDD and system is fine and responsive... compiz is working full throttle as the files are being copied...

thank you very much!

anyway what is the difference with AHCI and IDE modes?
which is better?
I am very happy that this help you, I know how can be frustrating something like this. :D

AHCI is some intel invention and under windows you have to use some of their special driver... It main purpuse is that in AHCI mode you can use some drive options that servers benefits from it like NCQ. Just use mode which have less problems, check wikipedia for more detail.

---

### Post by Mononofu on 2009-06-30
I have the same problem, also only since 9.04. This happens no matter if I use internal or external drives (connected via eSata), and is quite annoying, since I'm routinely moving around Full-HD movies.

I don't have a clue why this happens, but I know that it doesn't have anything to do with ext4 - ntfs and ext3 show the same symptoms. I'm only using SATA drives, maybe this could be part of the problem? (Still, why only in 9.04?)

---

### Post by jsravn on 2009-07-01
I had the same exact issue, intel board with SATA drives and AHCI enabled. 64-bit w/ ext4fs. Moving to 2.6.29 did not help. Extremely high cpu usage whenever doing any file access, slowing my system down.

Disabling AHCI in the bios fixed the problem.

---

### Post by infirmus on 2009-07-01
> **jsravn said:**
> I had the same exact issue, intel board with SATA drives and AHCI enabled. 64-bit w/ ext4fs. Moving to 2.6.29 did not help. Extremely high cpu usage whenever doing any file access, slowing my system down.

Disabling AHCI in the bios fixed the problem.

And again, I have the same issue. I'm running a custom 2.6.30 kernel. Does anyone know of a launchpad bug number for this?

---

### Post by Mononofu on 2009-07-01
And I can't even disable AHCI in my BIOS - sadly the laptop manufacturer didn't think the BIOS was actually meant to configure something . . .

---

### Post by HaMF on 2009-07-21
Same Problem here. (Asus V1S. When copying large files or accessing videos etc. which are located on the external harddisk) The System gets _really_ slow.

Some friends also reported the same problem. I'll try to disable AHCI but somethings wrong here with Ubuntu*. This problem should really be adressed imho.

*EDIT: No such setting available.

---

### Post by running_rabbit07 on 2009-07-21
Maybe as part of the change from EXT3 being fast but causing fragmentation, to fix the fragmentation problem the EXT4 has to go a little slower and use more resources?

Just a thought.

---

### Post by krams915 on 2009-11-19
Any solutions yet for this problem? I'm also experiencing huge slow downs when copying from ext3 to NTFS USB external drive. Computer becomes unresponsive. Firefox greys out.

When the copy process is finish, everything returns to normal.

I'm using 9.04.

---

### Post by Mononofu on 2009-11-19
Not really, I experience the same slowdowns now with Ubuntu 9.10. This also happens when copying between other ext# systems, so ntfs is only part (albeit a big one) of the problem.

---

### Post by krams915 on 2009-11-19
> **Mononofu said:**
> Not really, I experience the same slowdowns now with Ubuntu 9.10. This also happens when copying between other ext# systems, so ntfs is only part (albeit a big one) of the problem.

Thanks for the reply. If this is happening still with Ubuntu 9.10 then the problem seems to be really related with the kernel. I've done some research and here's an interesting link you might wanna check out:

Bug 12309 -  Large I/O operations result in slow performance and high iowait times   
[http://bugzilla.kernel.org/show_bug.cgi?id=1230](http://bugzilla.kernel.org/show_bug.cgi?id=1230)

(It's quite disappointing though because until now the bug hasn't been fixed, but at least they're working with it).

---

### Post by Mononofu on 2009-11-19
Yeah, I already stumbled upon this bug report, but since they had no solution either, I just reformatted all my data partitions to ext2.

btw, you seem to have posted a different link

---

### Post by adbge on 2009-12-24
I experienced this issue on kernel 2.6.31. While moving large files around on a separate HDD, the system would hang and become virtually unusable. Strangely, CPU usage, disk I/O and memory usage were far below capacity.

Solved this by booting into BIOS and toggling IDE to AHCI. System is now usable while under the same load and my write throughput has actually increased.

---

### Post by niksakl on 2010-03-04
I have the same problem here and I've been trying to solve it for a long time, but with no success...
I have tried changing my hd settings in the bios menu but with no result. Unfortunately I have no AHCI option on the menu.
I have also tried other Kernels, but no luck.

Please help me out, it drives me mad!

PS: My mobo is P5KPL-AM, CPU Q9550, 2GB RAM, running Kubuntu 9,10 64 bit.

---

### Post by psypher on 2010-03-23
I feel your pain. IMHO this is the worst bug I have ever encountered in linux as it happens to me 30% of my workday and has been doing this since Feisty (I think, it's been so long I can't remember exactly when). It feels like I am using Windows 3.1.

But unfortunately from what I can from this kernel bug ([12309]("https://bugzilla.kernel.org/show_bug.cgi?id=12309")) that this is still no solution to this problem and it seems someone is actively working on it. Despite that bug being marked as RESOLVED INSUFFICIENT_DATA I do see [recent work being done on this]("http://lkml.org/lkml/2009/1/17/123"). There is even a [Slashdot article]("http://it.slashdot.org/article.pl?sid=09/01/15/049201") about the bug. And from what i can tell there, there are a lot of people and distro's affected. So unless you are a l337 k3rn3l h@x0r and chums with Linus, we just all gonna have to wait..... aaaarrgg.

I for one and more than happy to throw money at the problem.

---

### Post by JesperSP on 2010-09-23
I have exact same the same problem under Ubuntu 10.04 - I have a Dell Vostro 1500 laptop with a Samsung 640GB HD.

Problem is really visible when trying to clone a VirtualBox VDI - I cannot use my laptop until the cloning is finished, and windows become grayed if attempting to use them. IMHO this is a MAJOR bug in Ubuntu - I hope someone is working on this, because otherwize I'm back to windøws :(

Cheers,
Jesper

---

### Post by psypher on 2010-09-23
Some progress has happened with this bug. Follow this thread: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

Affects almost all linux distro's

---

### Post by JesperSP on 2010-09-25
Thanks for your reply.. I decreased the swappiness of my installation to 10 and it appeared to increase overall responsiveness of the system during every day usage. But it is still slowed down by heavy file operations, but its not as bad as with the default 60 setting for 10.04.

(It is possible that another bug may have been fixed meanwhile)

Cheers,
Jesper

---

