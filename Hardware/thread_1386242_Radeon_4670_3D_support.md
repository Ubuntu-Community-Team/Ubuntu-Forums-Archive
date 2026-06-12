---
title: "Radeon 4670 3D support?"
date: 2010-01-20
forum: Hardware
---

### Post by Name141 on 2010-01-20
Would I have the ability to play my games from Steam (Unreal Pack , Half-Life2 pack , and America's Army for now) if I go over to Ubuntu now that I have switched over to an ATi video card?

---

### Post by kitserve on 2010-01-21
Hi Name141, 

I don't have any experience with the specific card, so take what I say with a pinch of salt - *but* I recently got a Radeon HD 3850 and have not had any problems with it in Ubuntu. I'm using ATI's binary drivers as the open source radeonhd driver isn't yet there on 3D performance. I have found that performance for DirectX games in wine is worse than what I get running it directly in XP but still perfectly usable. Whether that's related to the graphics card or the system as a whole I'm not sure, my rig is several years old and the graphics card is by far the newest part.

---

### Post by Name141 on 2010-01-21
Hm, so I doubt I could use my games with that information?

---

### Post by kitserve on 2010-01-21
Counter Strike Source and Left 4 Dead are perfectly playable for me via wine, I'm using a 3GHz P4 with 2.5GB RAM along with the aforementioned graphics card. I don't know how the system requirements for them compare with the games you're asking about. 

Put another way, my experience with the ATI binary graphics drivers and this card has been fine. Previously I had a lower-end nVidia card using nVidia's binary drivers and saw a similar difference in performance between Windows and Linux. So, if you have problems I don't think they'll be because it's an ATI card but rather due to performance issues in wine's DirectX layer. Your mileage may vary, of course.

---

### Post by HolgerB on 2010-01-21
Hi Name141,

I have an ATI 4670 too and are trying to get it running with the FGLRX driver under Ubuntu 9.04 x64 with no to little success.
From my perspective I would stay away from ATI for gaming with Linux right now. May be this will change when the open source driver provide better 3D within a half year or so but currently ATI under Linux was a mess for me.

Right now I did a fresh install with Ubuntu 9.04 x64 on my other PC and after activation/installation of the restricted ATI drivers via Ubuntu standard tool my system freezes with black screen after the Ubuntu bootscreen. Situation with my ATI 4670 was not good with the latest Fedora Core either BTW.

I had an ATI 1900XTX running fine under Ubuntu 8.10 x64. Unfortunately AMD/ATI decided to drop the Linux support for this card...well, something that runs UT3 in 1280x1024 at max details fine must really be legacy. Who needs this anyway ? :)

So I decided to buy a newer ATI card (the 4670) in order to get working 3D under Linux again. Esp. since the NVidia alternative were either somewhat more expensive (9600GSO/9800GT) or much less performant (9400GT/9500GT). Well, no luck until here with my 4670. I do not feel like pluging in my 1900XTX or my X800GT again to get 3D support via OpenSource driver. So I wait...

The problem (Black screen / freezing system) seems to be very common when using fglrx under Ubuntu. Just google for "black screen ati 4670 ubuntu"

My other Ubuntu system has a GeForce 7900GS which runs without a hickup. No driver issues. No problems when upgrading from Ubuntu 8.10 to 9.04.

Guess my next graphic adapter will be a NVidia card again.

Sorry for the rant but I hope you do better with your card.

Cheers,
HolgerB

---

### Post by Name141 on 2010-01-23
Looks like I'll be staying in XP for a while.

---

### Post by kitserve on 2010-01-25
Well, if you've already got the card I reckon you should give it a try, you've got nothing to lose!

---

### Post by markbuntu on 2010-01-25
> **HolgerB said:**
> Hi Name141,

I have an ATI 4670 too and are trying to get it running with the FGLRX driver under Ubuntu 9.04 x64 with no to little success.
From my perspective I would stay away from ATI for gaming with Linux right now. May be this will change when the open source driver provide better 3D within a half year or so but currently ATI under Linux was a mess for me.

Right now I did a fresh install with Ubuntu 9.04 x64 on my other PC and after activation/installation of the restricted ATI drivers via Ubuntu standard tool my system freezes with black screen after the Ubuntu bootscreen. Situation with my ATI 4670 was not good with the latest Fedora Core either BTW.

I had an ATI 1900XTX running fine under Ubuntu 8.10 x64. Unfortunately AMD/ATI decided to drop the Linux support for this card...well, something that runs UT3 in 1280x1024 at max details fine must really be legacy. Who needs this anyway ? :)

So I decided to buy a newer ATI card (the 4670) in order to get working 3D under Linux again. Esp. since the NVidia alternative were either somewhat more expensive (9600GSO/9800GT) or much less performant (9400GT/9500GT). Well, no luck until here with my 4670. I do not feel like pluging in my 1900XTX or my X800GT again to get 3D support via OpenSource driver. So I wait...

The problem (Black screen / freezing system) seems to be very common when using fglrx under Ubuntu. Just google for "black screen ati 4670 ubuntu"

My other Ubuntu system has a GeForce 7900GS which runs without a hickup. No driver issues. No problems when upgrading from Ubuntu 8.10 to 9.04.

Guess my next graphic adapter will be a NVidia card again.

Sorry for the rant but I hope you do better with your card.

Cheers,
HolgerB

The 4670 was not released until after the driver that you get with hardware drivers in jaunty so you need to use the latest driver from ati with that card and the 4770 and the 5xxx cards also.

---

