---
title: "Wireless Adapter Recommendation Please."
date: 2010-02-27
forum: Hardware
---

### Post by rcayea on 2010-02-27
Hi everyone,

First, I seriously tried to sift through these forums, especially the compatibility list to find a piece of hardware that will help me with my issue. It is just so tedious and the search feature just isn't helping. 

So, if you could please recommend a wireless usb adapter or wireless pci card that will work with ubuntu that would be much appreciated. I have a linksys wrt120n router and it works great, but as has been documented all over these forums, the wusb600n adapter is just not connecting and I am not hardware sophisticated enough to get it to work. 

Thanks for your recommendations,
Randy

---

### Post by 73ckn797 on 2010-02-27
Have you tried "ndisgtk" from Synaptic? You can install the Windows driver with that for the wireless card. I have successfully done that with a Trendnet card.

---

### Post by rcayea on 2010-02-28
Yes, I have tried that. Still no luck. I am willing to part with the wusb600n if there are any suggestions out there for a different USB adapter.

---

### Post by 2hot6ft2 on 2010-02-28
Since your router is N and the card is N I take it you want to make use of the N speeds. So since it's going to be extremely hard to find one that doesn't use Ralink I suggest you follow this guide and you want the RT3070STA driver not the RT2870STA driver in order to get the speed.

I have a Belkin with the same chipset and it worked for me.
[RALINK RT2870STA and RT3070STA USB WiFi Tutorial]("http://ubuntuforums.org/showthread.php?t=1342593")

Aside from that I've tried for months to find a N usb with a different chipset without any luck so that leaves you with G band. The Realtek RTL8187L chipsets generally work real good out of the box. The "alfa awus036h" is one and the "GSKY Realtek 500mW USB wireless adaptor" is another. They both have the RTL8187L chipset and can be found on eBay.

---

### Post by rcayea on 2010-02-28
Thanks a bunch for the information. I am going to go with one of the USB devices you suggested.

---

