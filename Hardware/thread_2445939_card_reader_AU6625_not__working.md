---
title: "card reader AU6625 not  working"
date: 2020-06-22
forum: Hardware
---

### Post by amirwe on 2020-06-22
Hi,

I installed Ubuntu 20.04 on Hp-Pavilion -15 dk.
My sd-card reader is not working.
I have Alcor Micro AU6625 PCI-E Flash card reader controller which shows under lspci as:

04:00.0 Unassigned class [ff00]: Alcor Micro AU6625 PCI-E Flash card reader controller

Please help

---

### Post by Yellow Pasque on 2020-06-23
It needs kernel 5.6 or later.  Googling shows that it may still have issues though.
[https://github.com/torvalds/linux/commit/444972b2b268c3272d39105bdc8d1266177f5d42#diff-d84246538d058655a36c3956a11f99b8](https://github.com/torvalds/linux/commit/444972b2b268c3272d39105bdc8d1266177f5d42#diff-d84246538d058655a36c3956a11f99b8)

---

### Post by jjmiler on 2020-09-22
08:00.0 Unassigned class [ff00]: Alcor Micro AU6625 PCI-E Flash card reader controller
ubuntu@ubuntu:~$ uname -mr
5.8.0-18-generic x86_64
ubuntu@ubuntu:~$ 
it seems a 5.8 kernel doesn't work

---

### Post by Yellow Pasque on 2020-09-22
> **jjmiler said:**
> it seems a 5.8 kernel doesn't work

So you tried the card reader? Are there any clues in dmesg after you plug in a card?
```
dmesg | tail -n 20
```

---

### Post by jjmiler on 2020-09-22
ubuntu@ubuntu:~$ sudo dmesg | tail -n 20
[ 3441.576804] OOM killer enabled.
[ 3441.576805] Restarting tasks ... 
[ 3441.578505] mei_hdcp 0000:00:16.0-b638ab7e-94e2-4ea2-a552-d1c54b627f04: bound 0000:00:02.0 (ops i915_hdcp_component_ops [i915])
[ 3441.578505] done.
[ 3441.579002] thermal thermal_zone9: failed to read out thermal zone (-61)
[ 3441.586010] PM: suspend exit
[ 3441.628659] Generic FE-GE Realtek PHY r8169-700:00: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-700:00, irq=IGNORE)
[ 3441.772955] r8169 0000:07:00.0 eno1: Link is Down
[ 3441.876203] mmc0: error -84 whilst initialising SD card
[ 3442.173722] mmc0: error -84 whilst initialising SD card
[ 3442.473020] mmc0: error -84 whilst initialising SD card
[ 3442.775130] mmc0: invalid bus width
[ 3442.775134] mmc0: error -22 whilst initialising SD card
[ 3447.028434] wlo1: authenticate with e4:9e:12:8a:b9:2d
[ 3447.030817] wlo1: send auth to e4:9e:12:8a:b9:2d (try 1/3)
[ 3447.056596] wlo1: authenticated
[ 3447.060469] wlo1: associate with e4:9e:12:8a:b9:2d (try 1/3)
[ 3447.064201] wlo1: RX AssocResp from e4:9e:12:8a:b9:2d (capab=0x411 status=0 aid=3)
[ 3447.070049] wlo1: associated
[ 3447.089069] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
ubuntu@ubuntu:~$

---

### Post by Yellow Pasque on 2020-09-22
>  mmc0: invalid bus width

I don't have any suggestions other than trying another card.

---

### Post by CelticWarrior on 2020-09-22
> **Yellow Pasque said:**
> I don't have any suggestions other than trying another card.

I second this suggestion.

---

