---
title: "DVB-T USB the are guaranteed to work in Linux?"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by monstermunch on 2007-12-09
Hi,

I bought a Freecom USB DVB-T TV viewer a few months ago. It worked with no hassle at all in Gutsy and I got great reception, picture quality and low CPU usage from it. It stopped working last week though, so I had a replacement sent to me. However, the one I was sent (the box is slightly different and the warranty is reduced by 1 year but everything else looks the same) has a completely different chipset inside that isn't supported. :'-( I found some posts saying the new version uses a realtek chipset and realtek have actually released the drivers for it but I need to wait for the release and will have to run a modified kernel (I think).

Now I have the situation of trying to get a replacement/refund when I've opened the packaging and it works in Windows but not Linux, which is really annoying. I'm actually quite happy to get a replacement, but I might get a different chipset again.

Is there any USB TV sticks that are guaranteed to work in Linux? I want to order a good one and not have the problem of praying that the chipset hasn't been changed recently.

---

### Post by MrHippocampus on 2007-12-09
The Linux DVB wiki holds lists of the majority of working/non working DVB devices, the list for USB DVB-T devices is [here]("http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices"). Some of the devices have their own special pages which have more information on specific problems (if any) with the device.

---

### Post by monstermunch on 2007-12-09
> **MrHippocampus said:**
> The Linux DVB wiki holds lists of the majority of working/non working DVB devices, the list for USB DVB-T devices is [here]("http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices"). Some of the devices have their own special pages which have more information on specific problems (if any) with the device.

Thanks for the feedback. I found that list but the problem is, which ones can I order and be sure they will work in Linux? My freecom stick is on that page as supported and unsupported depending on the chipset used inside. As far as I can see, there is no way for me to check what chipset is being used without buying it, opening the package and trying it (so I might not get a refund if it doesn't work).

I read about the WinTV NOVA-T quite a lot. I'm tempted to get that because it seems to be very well supported but I'm worried I'll get burned by the same problem.

---

### Post by MrHippocampus on 2007-12-09
Yes, getting a different chip in the same box is a big problem (exactly the same thing happens with wireless USB devices), unfortunately theres not much you can do other than try it and see if it works, if not, putting it on ebay is always an option.
In some cases the manufacturer will replace the device for you, this happened with the nova 500 pci, the chip changed and the linux DVB people said they wouldn't make a driver for it because the chip wasnt manufactured for very long, so hauppague let people return the new version and they were given an old version back.

Anyway, as you say the nova-t looks like a good choice, however I would recommend looking at the recent linux DVB mailing list archives for the latest info on any possible problems with the device you want to buy, [link]("http://www.linuxtv.org/pipermail/linux-dvb/").

---

