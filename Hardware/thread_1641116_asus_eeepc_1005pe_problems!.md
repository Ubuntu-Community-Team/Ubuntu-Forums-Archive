---
title: "asus eeepc 1005pe problems!"
date: 2010-12-08
forum: Hardware
---

### Post by dumble on 2010-12-08
**A little history first**
My girlfriend got a ASUS EeePC 1005PE (2 weeks ago). Win7starter pre-installed. I then installed win7ultimate. A few days later, BSOD memory management. I had a clean install, clean disk, all drivers. So I did a memtest. It gave 9 errors.

So weird, new netbook and RAM problems. So to make sure. I used another USB flash, with memtest and tested again in another USB-port. Tested again, no errors. Then I tested 3 more times, sometimes I let it run more then 24 hours and I still got no errors. The bluescreens however were still not over. So I also started testing the harddisk. Used seatools for the Seagate harddisk thats inside of this netbook. It gave no errors. 

I went to the shop, because bluescreens did not stop. And it takes 3 weeks for techservice to test it and then fix it or give you a new one takes up to 3 months. The problem is, we go on a world-trip in 5 days. So no time!

I then decided to install Ubuntu. Maybe it was not a hardware related problem I thought, so that will be fixed by installing Ubuntu. That was the plan anyway, to try out the new netbook edition. So I downloaded the Ubuntu 10.10 netbook edition. And used unetbootin to put it on a USB flash. Checked the disk for errors first, no errors.

Then I tried installing, I created the partitions manually
[LIST]
[*]sda1 - Swap - 4GB - primary
[*]sda2 - Ext4 - 45GB - primary - \(root)
[*]sda3 - Ext4 - 200GB - primary - \home
[/LIST]
(see attachment)
*sda4, Is I think where Express Gate is installed. This is the ASUS (linux-based) OS that boots in 5 seconds.

Anyway, after I created the partitions, I chose Install. It then starts creating, and after that copying files. And there is where it goes wrong. At about 1/3 of copying, it gives an error that installation failed.

So this is a Hardware problem? Or not? What can I do? Just buy new ram I think.. or has someone any other suggestions.. 


ps
In win7starter, which was working fine without BSOD (but only used it for 4 days or something). I updated the BIOS to the latest revision from asus website.


EDIT
I SOLVED the problem. There RAM was faulty, I put 1GB ram of my older system inside. No problems now

---

