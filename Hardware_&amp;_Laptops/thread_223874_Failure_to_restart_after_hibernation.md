---
title: "Failure to restart after hibernation"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by yahya.mohamed on 2006-07-27
Hi,
The problem I am having is:

-------------------PROBLEM---------------------------------------------
If I hibernate ubuntu, then it will not restart the next time if I load my windows partition before restarting, if I hibernate and restart ubuntu directly (no loading of windows in the middle, then all works fine).

Does anyone know what is going on?

-------------------BACKGROUND INFORMATION-------------------------------
Using Toshiba Satellite A25, P4, 2.66GHZ

I have to say that I began having this problem after I tried fixing another problem that occured during booting, which was a message saying 

There are differences between boot sector and its backup................

I attempted to fix this by issuing the following:
sudo dosfsck -ar /dev/hda1     where hda1 is my windows partition.

I think the two are related!

Thanks in advance

---

