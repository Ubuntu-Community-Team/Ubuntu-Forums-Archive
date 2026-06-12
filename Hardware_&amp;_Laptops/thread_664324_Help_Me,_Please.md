---
title: "Help Me, Please"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by masuti on 2008-01-11
Hi all, My name Ali. I had some problem with my wireless. I'm using Presario 2551EU laptop, and had built in wireless Wifi (Broadcom 802.11b/g WLAN). when i connect true wire internet (Direct from modem) no problem, i can surf internet as well. but when i try connect using my wireless, I never ever get conected to internet. Ok here my spect:
- Laptop  : Presario M2551EU
- OS        : Ubuntu 7.04
- Router  : Linksys WAP54G V3.1
Please help me, coz i'm so tired with my WIN XP, even i had ORiginal copy and already paid:(.

---

### Post by stalker145 on 2008-01-11
> **masuti said:**
> Hi all, My name Ali. I had some problem with my wireless. I'm using Presario 2551EU laptop, and had built in wireless Wifi (Broadcom 802.11b/g WLAN). when i connect true wire internet (Direct from modem) no problem, i can surf internet as well. but when i try connect using my wireless, I never ever get conected to internet. Ok here my spect:
- Laptop  : Presario M2551EU
- OS        : Ubuntu 7.04
- Router  : Linksys WAP54G V3.1
Please help me, coz i'm so tired with my WIN XP, even i had ORiginal copy and already paid:(.

Hi, Ali. First off, we need to figure out what kind of Broadcom card you have. Specifically, what chipset, model, etc. Most of that information *should* be in your manuals (model, anyway) and you can also find it by typing ```
lshw
```into the terminal and looking for an entry that mentions wifi0, ath0, or something similar and has your Broadcom information on it.

The next step would be to check the [Hardware Compatibility List]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom") for your card to see if there are any special instructions for getting it to work.

Don't hesitate to check back if you run out of ideas or need more help.

---

### Post by jespdj on 2008-01-11
That should have been
```
lshw
```
and not **lswh**

---

