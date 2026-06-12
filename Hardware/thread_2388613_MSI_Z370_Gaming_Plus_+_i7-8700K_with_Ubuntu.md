---
title: "MSI Z370 Gaming Plus + i7-8700K with Ubuntu"
date: 2018-04-05
forum: Hardware
---

### Post by pt12lol on 2018-04-05
I am considering buying MSI Z370 Gaming Plus mobo with i7-8700K CPU and I am wondering what Ubuntu users experience is. I found hardly anything about this mobo with Ubuntu, except issue with maximal screen resolution with Ubuntu (which is actually - as I found in other sources - connected with Z370 chipset, not only with this mobo). I am going to plug in two displays, one with 1080x2560 resolution and another one with 1080x1920 resolution, so I hope this issue doesn't involve me? Do you have any experience with this mobo and this CPU? Experienced any other issues with its subcomponents? Maybe you have any other good purchases working with Ubuntu for this CPU? I'd like to use Ubuntu LTS edition, the best 18.04.

---

### Post by oldfred on 2018-04-05
While not same brand, shows Z370 works, but needs newer kernel. You may need 18.04, but realize it is not released and may have some issues or even require total reinstall. 
Two years ago I built a new system with Z170 and a couple of months before 16.04 was released installed it. It worked well, but I had my older system to fall back to if I had major issues.
What video card or using internal video?

ASUS PRIME Z370-A Running Great On Linux, needs i915.alpha_support=1 or Linux 4.15 kernel
 [https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1](https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1)
ASRock Z370M-ITX/ac: Mini-ITX Motherboard With Dual NICs, WiFi, Triple Display For ~$130 USD Oct 2017
[https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1](https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1)

---

### Post by miles-rumppe on 2018-04-21
I built a system with the MSI Pro Carbon Z370 with the 8700K w/ 16GB of ram in it and it's purring like a kitten.  I had an issue with the PSU I originally went with though and have since replaced it due to low voltage causing a boot failure.  I picked up the board on Newegg for $130 w/ a rebate attached to it.  When the PSU failed the mobo was flashing the CPU light which can be a bit misleading as the CPU was fine and there wasn't any issue there.  Anyway in a week 18.04 is being released and 17.10 has been working just fine for the past couple of months while waiting.  

I wouldn't worry too much about this board or that board since they're all based on the same HW since it's a new CPU that was released.  I used the i915 line mentioned above and got 4K resolution working w/o a hitch.  Don't bother trying to mess with the drivers or microcode with any of the boards.  

Dual displays can be handled easily with the HDMI/Display Port options on the mobo as well.  More displays though would require a dedicated GPU to add the functionality to most mobo's.  The hd 630 on the cpu works just fine though for day to day activities / transcoding for Plex as well.  Kind of depends on what else you're planning on doing with it.  BTW liquid cooling isn't needed either if you have a good heat sink on it as well.  I'm usually in the 30C range and it might spike to 60 if there's some processing going on in the background for video files.

I built mine with a few things in mind: NAS/WIFI AP/Router/etc to consolidate my multiple devices.
- NVME for OS / boot
- HDD for storage
- 2 x 4 port gig NICs for bundling / aggregation of traffic inside/outside
- quad tv tuner for Plex recordings
- tried using my intel 9260 for WIFI/WAP but, it didn't work so well and put in a WLE1216 from Compex for Hostapd to work correctly
- 16GB of ram (Team)
- 6 x 120mm fans throughout the case / CPU 

It's normally whisper quiet until a reboot and the spin up during POST

---

