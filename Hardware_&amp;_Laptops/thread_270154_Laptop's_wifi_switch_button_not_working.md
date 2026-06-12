---
title: "Laptop's wifi switch button not working"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by jogogets on 2006-10-02
I have a Medion MD 97000 laptop. The internal ipw2200BG is switched on by pressing a dedicated button on the laptop. After install I configured my wlan to a static IP address. However, the wifi is not active. I ran the command sudo lshw and I got this:

driver=ipw2200 driver version 1.1.1 firmware= ABG 9.0.2.6(MAR 22 2005) ip=119121.168.0.2 link=no multicast=yes wireless=radio off

I also have a "SIOCGIFFLAGS error No such device" appear when I open up my network connection icon. 

Any ideas? I have read a large number of forum threads and tried a few things but I believe I need to identify how to switch the wifi device on by either having the wifi switch recognised or reconfiguring the keyboard. 

Any help will be appreciated.

---

### Post by n3Cre0 on 2006-10-04
I had this a couple of times and I just went to BIOS and put the radio on again.

When rebooting press F2. Just look around there abit - you'll probably see that the onboard wifi is "Disabled", put it on "Last State"

---

### Post by jogogets on 2006-10-04
Thanks Ncr3o, that worked. I had to setup the BIOS then logon to windows, switch on the wifi then reset. Funny thing is I can switch the wifi off from Ubuntu using the button that won't switch it on. Go figure.:KS

---

