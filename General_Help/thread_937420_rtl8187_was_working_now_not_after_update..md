---
title: "rtl8187 was working now not after update."
date: 2008-10-03
forum: General Help
---

### Post by timmo710 on 2008-10-03
Hi all,

My wireless decided one day after updating that it would not connect to my wireless network anymore.
I have ubuntu 8.04. My laptop was setup by myself for security auditing. So naturally I had patched the drivers allowing for injection. This all was working fine. Airodump was also working fine and could inject and all. Have 3 cards with the same chipset and all 3 worked fine. Also have internal ipw2100 wireless that's gutless and only has 802.11b.

I just installed an update 2 nights ago and now when I plug the wireless card in, it is now wlan3 instead of wlan0, will not connect to any access point, and airodump shows all access points and clients as having no power. the internal card works fine though. just the driver for the RTL8187 doesnt want to work properly.

I have tried reinstalling the patch driver but it doesn't want to work

Has anyone else had this issue? Its just killed a great system that functioned better than windows, now I might as well use windows.

Any help would be great

---

### Post by timmo710 on 2008-10-06
*bump bump*

anyone have the same issue and found a solution. anyone with issue looking for someone to work with around this?

have tried the cards in other os (backtrack) and it works without an issue

---

### Post by timmo710 on 2008-10-06
just got another wireless card (D-link DWL-650+) shows up as wlan5. also doesnt show any power in airodump-ng. plugged system into network with a cable and tried more updates. just waiting on a restart before i test that. 

at least now i know its not an issue with the driver (unless its to do with ieee80211)

anyone with ideas? will try almost anything

---

