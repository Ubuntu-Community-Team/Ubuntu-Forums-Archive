---
title: "moto4lin - need help"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by ATIuser on 2008-01-05
I've been looking all over the net for a way to get this program to work, but I have yet to find one.
Heres the thing, I ran lsusb and my Razr v3m shows up. However, when I run p2ktest the vendor id and product id are there, but there is no information as to the phone model...and I get a message saying no phone was found.

When I run moto4lin the program connects in P2K mode just fine, but it is unable to get info on the phone model, files, drive etc.

Whats wrong?

---

### Post by foolsh on 2008-01-05
yeah this ones tricky
I have a v235 camera phone it took me awhile to get moto4lin to work
the stupid id numbers change if you don't get it right so unplug and plug back in your phone if it doesntt work.
I think the steps are
1 run moto4lin as root "sudo moto4lin"
2 plug in phone
3 goto preferences click update list, choose device  and write down the AT vender and product ID
4 exit moto4lin unplug phone
5 run moto4lin as user "moto4lin"
6 goto preferences and enter the AT Vendor and Product ID in their fields 
7 enter the AT Vendor ID into the P2k vendor ID field 
8 enter the AT Product ID minus 1 into the P2k Product ID field
ie
AT Vendor ID 22b8
AT Product ID 4902
P2K Vendor ID 22b8
P2K Product ID 4901
9 enter the right dev path mine is "/dev/ttyACM0" run dmesg it should tell what yours is in the log
10 exit moto4lin pray to your god sacrifice a chicken and cross your eyes
11 run as root again "sudo moto4lin" plug in phone
12 click connect see if it worked



I'm not around my home computer right now but when I get home I'll double check to see if that was right
 note: step 11 might be run as user "moto4lin" now that I think about it.
hope this helps

---

### Post by ATIuser on 2008-01-05
I noticed that the vendor/product ID's kept changing so I followed tutorial that said to modify ~/.qt/moto4linrc with the correct information so I've done that and it doesn't ever change now. 

Some one else's tutorial stated that you need to be root to have access to the hardware so they suggested doing a sudo chmod u+s /usr/bin/moto4lin to be able to run as a normal user with root privileges. I've done that.

Strange thing is, it connects fine in AT mode, then  switches to P2K mode and stays connected, it just can't retrieve any info:
> 
[info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 
[info] Phone answer: OK OK 
[info] Phone pluged as P2K
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get file count
[error] Unable to get drive name


Which is why I think it has something to do with P2K test not showing that any phone is found. Is there supposed to be a P2K driver that I don't have?

---

