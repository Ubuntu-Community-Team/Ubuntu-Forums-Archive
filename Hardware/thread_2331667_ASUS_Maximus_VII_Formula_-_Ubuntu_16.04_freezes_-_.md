---
title: "ASUS Maximus VII Formula - Ubuntu 16.04 freezes - solutions? Win10 runs stable"
date: 2016-07-24
forum: Hardware
---

### Post by maxbar on 2016-07-24
On my Maximus VII Formula, Ubuntu 16.04 64bit keeps freezing / locking up (meaning: requires hard reset / shut-off & turning back on) while leaving running overnight (only web browser open, low CPU and GPU utilization).

My HW other than the already mentioned mobo:

32 GB RAM
i7-4790K @ 4GHz
GTX Titan X

I use the proprietary drivers for 3 x display on the Titan X and the Broadcomm for bluetooth (keyboard) and WiFi. Other than that, just the default desktop install.

Has anyone else with this or similar mobo encountered Ubuntu keeps freezing / locking up and if so, what was the solution if any to fix that? I keep it updated automatically.

Thank you all for suggestions and whoever can resolve this for me - I really want to get away from using Win10, but I might have to go back to that if the freezing / locking up issue can't be resolved!

---

### Post by houstonbofh on 2016-07-25
Can you test with 14.04?  A few people have been having hard to identify stability issues with 1604 on specific hardware.  You may be one of them...  (And yes, I know this is not a good answer)

---

### Post by leozinho29_eu on 2016-07-30
Hi

I believe the issue is more related to the video card than the motherboard. My friend has similar freezes with his computer that uses a NVidia card too. Most of the times when that bug happens everything freezes, but sometimes the Skype calls don't freeze, it is just the video and inputs from keyboard and mouse that stops working.

We tried the LXDE interface (and Lubuntu), and we noticed that his computer was working for hours until it freezes, and then always the Skype calls did not freeze.

Opening Unity3D games made the computer to freeze near instantly.

And I had a similar issue with another NVidia card (this one is old) that happened with Windows XP. The computer froze after 10 minutes, unless if I opened some very specific software to keep the computer alive for more time.

There was some computers with NVidia cards I use Lubuntu and they are stable, but is noticeable that their fans are at 100% full time. Have you checked the card's temperature? If the system is not controlling the fan well, then it may be overheating.

---

