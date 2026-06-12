---
title: "Possible Ethernet port failure???"
date: 2011-07-16
forum: Hardware
---

### Post by nepabuntu on 2011-07-16
Hello everybody,
I've a Ubuntu 10.10 in hp dv6 laptop with the ethernet card from Realtek. Recently my LAN connection broke and I tested to see if it was the wire or the laptop's port. Then I found it was the laptop's port that was faulty.

The *lspci | grep -i ether* command still shows the ethernet controller so I guess its not the entire NIC that's damaged. I guess its the ethernet port that has been damaged.

> 
rizon@rizon-laptop:~$lspci | grep -i ether
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


Is there any possibility that any of the configurations disable the ethernet connection? Or it could be totally the hardware failure? If its hardware failure, is there anything I could do at home?

Regards
nepabuntu

---

### Post by dandnsmith on 2011-07-16
I've a couple of PCs which have ethernet controllers, but non-functioning ports. If you've tried a change of wire and router port, then it's almost certainly the port on your laptop.
Only thing you can then try is some sort of addon - USB ...
Have you tried booting from a LiveCD - if it is just your installation configuration at fault, you'll be able to see a working connection?

---

### Post by nepabuntu on 2011-07-16
> **dandnsmith said:**
> I've a couple of PCs which have ethernet controllers, but non-functioning ports. If you've tried a change of wire and router port, then it's almost certainly the port on your laptop.
Only thing you can then try is some sort of addon - USB ...
Have you tried booting from a LiveCD - if it is just your installation configuration at fault, you'll be able to see a working connection?

I am pretty sure is the port on my laptop as I've already tested with the live CD with no success. I am wondering if there's any way I could try to repair the port itself(any sort of tutos I can refer to). Otherwise I guess I will have to buy the USB one. Thanks for your reply

---

### Post by mexicanseaf00d on 2011-07-16
My DV7 showed a blinking LED when I connected LAN cables, no connection - sometimes wasnt even recoginzed by win/linux. I had to rip out the battery a couple of seconds (also the power cord, of course) and it worked again!

---

### Post by nepabuntu on 2011-07-16
> **mexicanseaf00d said:**
> My DV7 showed a blinking LED when I connected LAN cables, no connection - sometimes wasnt even recoginzed by win/linux. I had to rip out the battery a couple of seconds (also the power cord, of course) and it worked again!
Surprisingly that worked. Thanks a lot for sharing what you had experienced. :) :)

---

### Post by dandnsmith on 2011-07-16
With a blinking LED, I wouldn't be surprised at that working.

Glad it's fixed

Now all that remains is to mark the thread SOLVED

---

### Post by db260179 on 2011-07-16
I can suggest something be a HP DV7 owner. DV6 and 7 have a Realtek R8168 NIC, unfortunatley the r8169 driver loads, which doesnt work well with this nic. You need to download the correct driver from Realtek.com.tw

Then blacklist the r8169

Hope this helps?

> **nepabuntu said:**
> Hello everybody,
I've a Ubuntu 10.10 in hp dv6 laptop with the ethernet card from Realtek. Recently my LAN connection broke and I tested to see if it was the wire or the laptop's port. Then I found it was the laptop's port that was faulty.

The *lspci | grep -i ether* command still shows the ethernet controller so I guess its not the entire NIC that's damaged. I guess its the ethernet port that has been damaged.



Is there any possibility that any of the configurations disable the ethernet connection? Or it could be totally the hardware failure? If its hardware failure, is there anything I could do at home?

Regards
nepabuntu

---

