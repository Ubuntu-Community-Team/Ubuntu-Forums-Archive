---
title: "HP Pavillion dv6000z Hardy Heron"
date: 2008-04-25
forum: Hardware
---

### Post by chris.raighn on 2008-04-25
Well I installed 8.04 yesterday, all went fairly well. First the whole computer froze at 15 percent, so I restarted at tried again with success. I had heard about a bug in the dv6000z laptops for the acpi...Thats what I figured. I installed the Broadcom and NVidia drivers with no hassle. 

I do notice something with updating, while its downloading the repositories, it takes a while to download the lists on battery power. But if its plugged in, its quick. ACPI bug? I don't know about the sound still, it hasn't worked since HP last fixed it (Windows either). Touchpad is more sensitive and responsive than in Windows. I likey. So far so good.

---

### Post by chris.raighn on 2008-04-26
I also notice that the WLAN switch has to be turned on from boot-up, otherwise the wireless won't work if turned off and then on again from in Ubuntu.

---

### Post by gururise on 2008-04-26
Your lucky your wireless works... on my Hp dv6000z, my wireless wont work on Hardy, unless I compile a custom 2.6.25 kernel.  This is due to the broadcom drivers.  
Can you do a **lspci -nn** and post the results of your broadcom driver here?
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)
```

Notice mine says (rev 02).  I suspect yours is rev 01.

Also, does suspend/hibernate work for you?

---

