---
title: "Sorry for another WiFi thread"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by dancavallaro on 2005-09-25
I hate to make another Wifi thread, but I've followed the tutorials and i still can't get it to work...

I have a WPC54G v.3. I installed ndiswrapper. "cardctl status" gives me "3.3V CardBus card", but "cardctl ident" says no product info available. I can successfully install the LSBCMNDS drivers, but when I do ndiswrapper -e it detects the drivers, but no card. It seems as if my computer isn't detecting the card. However, PCMCIA does start at bootup. Any ideas as to what the hell is going on? I'm banging my head against the wall here.

---

### Post by dancavallaro on 2005-09-25
*bump*

I tried the broadcom tutorial, but that didn't work either. It seems  like the card isn't being detected or something.

---

### Post by mlomker on 2005-09-25
If your cardbus controller isn't working with Ubuntu then installing the drivers won't help, of course.  Do you have another card that you can insert to see if an ident works?

---

### Post by dancavallaro on 2005-09-25
I tried a couple different cards and they all worked, giving me some information when i did cardctl ident. So obviously the cardbus controller is working but i just can't get this damn card to work. I know people have gotten the WPC54G v.3 to work on Ubuntu so I don't understand why it won't work for me.

---

### Post by mlomker on 2005-09-25
Have you used the card in another machine or with Windows?  It could just be bad...

---

### Post by dancavallaro on 2005-09-25
Yeah I've used it in Windows, it works fine. Also, when I do iwconfig, it says 

lo       no wireless extensions.

sit0    no wireless extensions.

eth0   no wireless extensions.



ifconfig only shows lo, it doesn't show eth0 or wlan0 or anything like that.

---

