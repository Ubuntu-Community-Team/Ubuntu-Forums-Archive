---
title: "the wireless disappeared, after hibernate"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by hydrogen on 2006-07-22
Hi, I am using T42 installed Dapper, I want to enable the wireless led, so I do the following command:
echo 1 > /sys/bus/pci/drivers/ipw2200/0000:02:02.0/led
modprobe ipw2200 led=1
and the led work fine. but after hibernate, the wireless disappeared. 
How to fix the problem.
I have to reboot the machine to let my wireless work again.

Thank you

---

### Post by H.E. Pennypacker on 2006-07-23
When returning from hibernation, did you get a message saying "HAL failed to hibernate"?  If you did, your problem is similar to another user, so check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=197062&highlight=hal+failed+hibernate](http://www.ubuntuforums.org/showthread.php?t=197062&highlight=hal+failed+hibernate)

That thread may not actually provide a solution, but it is better for you to continue a thread rather than creating a new one, if it matches an older one.

---

