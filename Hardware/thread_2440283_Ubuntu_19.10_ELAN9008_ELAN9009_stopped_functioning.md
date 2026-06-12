---
title: "Ubuntu 19.10 ELAN9008 ELAN9009 stopped functioning due to kernel update"
date: 2020-04-08
forum: Hardware
---

### Post by tkluter on 2020-04-08
Hi all, 
I hope this is the correct forum to post this issue.
I'm running Ubuntu 19.10 on several machines with amongst others a Asus Zenbook DUO UX481 (the PRO DUO should also be affected (UX581)).
Up to kernel 5.3.0-18-generic the touchscreen of the second display was detected by the kernel (in my case an ELAN9009) and all worked nicely.
From kernel 5.3.0-42-generic the touchscreen is detected by i2c_hid, but not any more by hid-generic->input.
I've tried to find the updates in the driver that causes this problem, but am unable to find it.
I also tried Ubuntu 20.04beta to see if the problem might be solved in the "newest" kernel, but no the problem still persist, i2c detects it and hid-generic doesn't.
I would be very happy if either somebody could give me some hint to where to look, or to cooperate with somebody of the kernel development to give all required information on the ELAN9009 (and ELAN9008 as I will have in the near future the Asus Duo Pro (UX581) permitting the delays in delivery due to COVID-19).
Hope somebody can help me out, as I love this ASUS machine especially for on-line teaching and recording.
Kind regards and thanks for any help,
Theo Kluter

---

