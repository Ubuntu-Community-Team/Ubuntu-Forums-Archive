---
title: "No bluetooth ath9k"
date: 2010-05-11
forum: Hardware
---

### Post by luchonat on 2010-05-11
Hi, i have an acer aspire with ath9k chip providing wireless and bluetooth. I can't make the bluetooth work... It did not work in ubuntu 9.10, and now i upgraded to 10.04 and still does not work...
I've been looking everywehere and no clue...
when i do
service bluetooth start
nothing happens, and then
service bluetooth status
says that bluetooth is not running, just like if no device was detected...

i've found in 

[http://wireless.kernel.org/en/users/Drivers/ath9k/btcoex](http://wireless.kernel.org/en/users/Drivers/ath9k/btcoex)

this:

Bluetooth coexistence is automatically detected and enabled as of 2.6.32 so you do not have to do anything for it. For kernels older than 2.6.32 you can can enable bluetooth coexistence on ath9k by using the btcoex_enable module parameter, but you should not enable it unless you know you have one of the devices listed above.

And the kernel that came with 10.04 is 2.6.32-22

Anyone can help???
thanks a lot!!!
Excuse my english!

---

