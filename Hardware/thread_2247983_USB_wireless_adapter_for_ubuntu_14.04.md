---
title: "USB wireless adapter for ubuntu 14.04"
date: 2014-10-11
forum: Hardware
---

### Post by FannyG on 2014-10-11
Hi,

I'm running Ubuntu 14.04 on my laptop but the wifi won't work so I want to buy a USB wireless adapter. Do you know which wan runs "out of the box" with Ubuntu 14.04 ?

---

### Post by Vladlenin5000 on 2014-10-11
Most work "out of the box" currently but if I were to suggest one it be any device based on the Realtek 8191SU chipset.
The chipset inside is what you should be focusing on, nothing else. Many vendor release different hardware under the same brand/model and just add a different revision numbering to distinguish them. So, a dongle of the brand X, model Y (r.01) may work OOTB whereas the "same" brand X, model Y (r.02) won't.

---

### Post by Otto-C on 2014-10-13
Had great ease with:
Rosewill USB wireless adapter RNX-N180UBE

lsusb shows as:  0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

---

### Post by Vladlenin5000 on 2014-10-13
> **Otto-C said:**
> Had great ease with:
Rosewill USB wireless adapter RNX-N180UBE

lsusb shows as:  0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

Of course: RTL8191SU ;)
Now, Rosewill is mostly known in USA but there are many online store that can send it abroad. It's up to you to decide, considering the price (S&H increases the price substantially in international orders). You'll get the exact same results with a no-name from China with the same chipset. I have 3 still going strong and working almost 24/7 for years now.

---

### Post by Mike_Walsh on 2014-10-13
I've had great success with a TP-Link WN725N (v1) adapter. I've used it since I started with Ubuntu back in May. It was a bit spotty in the beginning, but ever since the 3.13-0.32 kernel update, back in late July/early August, it has worked flawlessly.

It uses the Realtek RTL8188CUS chipset. I would now have no hesitation in recommending this adapter to anyone. But do make sure to obtain the v1 version; apparently the v2 version has a different configuration, or something like that.

Regards,

Mike.

---

### Post by Vladlenin5000 on 2014-10-13
Version 2 probably has an entirely different hardware (chipset). That's typical of many vendors, aggregate under the same model those with similar characteristics/performance and just using what is cheaper at the time of release.

RTL8188CUS currently has indeed good support but I remember lots of people complaining no so long ago.

---

### Post by Mike_Walsh on 2014-10-13
Indeed! 

As I indicated in my post above, since the 3.13-0.32 kernel update it's worked perfectly. Prior to that, it was.....aggravating, to put it mildly..!

As you say, it's probably a case of what's cheaper at the time. In this case, they appear to have the same chipset (see [here]("https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1")), but I know people who've replaced v1 with v2, expecting improvements, and found that it works erratically, or not at all. C'est la vie...

Regards,

Mike.

Edit: AFAICT, the difference appears to be that v2 uses the EUS version of the 8188 chipset, as opposed to the CUS of v1..?

---

