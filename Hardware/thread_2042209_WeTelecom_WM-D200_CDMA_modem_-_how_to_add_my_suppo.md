---
title: "WeTelecom WM-D200 CDMA modem - how to add my support 'patch'?"
date: 2012-08-14
forum: Hardware
---

### Post by vincent33 on 2012-08-14
Hello, community!
I'm not sure if this topic should be posted in the wireless forum (seems there are mostly wi-fi related topics in it) or here, anyway I decided to post it here.
A month ago or so I bought a CDMA EV-DO Rev.A. wireless modem in my satellite ISP's local shop. As expected, it didn't work 'our of the box', but there were some solutions to fix that. I didn't like that 'manual' way of getting it to work each time I reinstall the OS and there was a speed 'limit' issue, so I started to dig and thought up another solution.
Now it all works just fine but:
1) I gotta re-apply my 'patch' each time after the kernel update
2) It still doesn't work out of the box, I guess a lot of people get pain in some place when they buy it
So my question is:
**Where can I find people who will explain me whether my solution is good (and maybe improve it a bit) or not, and after that how would I be able to make it available for other people (like push it into a new kernel or so)?**
I may sound funny since I just have NO experience in programming and such stuff, I just want to make it a bit easier for other people who won't be looking for a normal solution on the net.
And now about the solutions I saw.
1) use modprobe usbserial product=... vendor=... command to get the modem working. I had a sort of speed limit with that, speed just never exceeded ~512 kb/s (62.5 kB/s or so)
2) edit drivers/usb/serial/option.c in the kernel, add 'support' for your modem manually and compile your own usbserial modules to replace the original option.ko with your own, then add 'option' module to autostart list (/etc/modules).
I just don't know where to go and who to ask about all this.
I can provide your with some extra information if needed.
By the way:
```

Manufacturer: QUALCOMM INCORPORATED
Model: 239
Revision: WM-D200R-AJ30-SKYLINK  1  [Mar 27 2007 13:00:00]
ESN: 0x15BDD11
+GCAP: +CIS707-A, CIS-856, +MS, +ES, +DS, +FCLASS

```

---

### Post by vincent33 on 2012-08-15
it seems that no one knows?

---

