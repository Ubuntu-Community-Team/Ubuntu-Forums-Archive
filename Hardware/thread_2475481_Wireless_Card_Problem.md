---
title: "Wireless Card Problem"
date: 2022-05-28
forum: Hardware
---

### Post by wjbmd48 on 2022-05-28
Hi:

I'm running Lubuntu 22.04 on a Thinkpad T430s.

I have a wireless problem that confuses me:

1) Wireless light above keyboard off, and of course, no wireless connection.
2) Yes, the hard wireless switch is on, switch shows green.
3) Replacing the wireless card with a good one doesn't fix the problem
4) When I swap the HDD into another T430s, wireless works fine, so I don't think it's config file/software.

Here's what happens when I go through an rfkill cycle:

bill@T430snew:~$ rfkill block all
bill@T430snew:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
bill@T430snew:~$ rfkill unblock all
bill@T430snew:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

Ie, unblocking with rfkill doesn't fix the problem.

A. Any ideas?
B. I'm happy, if this is too much trouble to fix, to go with a USB dongle, but I've not had good luck with the linux drivers from commercially available ones.  Does anyone have any recommendations for one with solid Linux support?

Thanks!

Bill

---

### Post by #&amp;thj^% on 2022-05-28
newer kernels and some drivers like nvidia, are in progression state :IE
```
inxi -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169

```
No wireless even detected, but:
```
rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
```
VGA compatible controller: NVIDIA Corporation TU117M [GeForce GTX 1650 Ti Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 10fa (rev a1)
02:00.0 Non-Volatile memory controller: Sandisk Corp WD Black SN750 / PC SN730 NVMe SSD
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)

```
best recall of testing kernel 5.11 was the last reliable use of WiFi. :(
and your 2 T430's may have different WiFi cards.
I'm going to swap one out to an older pci chip, I'm not sure how that will work out.
BTW I'm certainly  not recommending using a unsupported kernel though.

---

### Post by wjbmd48 on 2022-05-28
Thanks!

But I'm pretty sure that the problem is specific to the box: when I swap the wireless card and the HDD into another box, everything works fine.

So I'm guessing there's no easy fix. What will likely work is a dongle, and what I really need, I think, is a reliable one with a good Linux driver, which I've not been able to find.

Thanks!

Bill

---

### Post by #&amp;thj^% on 2022-05-28
> **wjbmd48 said:**
> Thanks!

when I swap the wireless card and the HDD into another box, everything works fine.

Bill
I did not see switched both, that was kind of a blur to my minds eye. ;)

here's some with linux support: [https://www.amazon.com/linux-wireless-adapter/s?k=linux+wireless+adapter](https://www.amazon.com/linux-wireless-adapter/s?k=linux+wireless+adapter)
did you test with different USB ports, if that's the connection used. you don't say.

---

### Post by wjbmd48 on 2022-05-28
OK, thanks! I get a good connection with ethernet and an ethernet to USB adapter, so I'm guessing it's a screwy hardware problem that'll be too hard to find and fix. 

I've got a brand spanking new card on order, and if that doesn't work, I'll go with the USB dongle.

Thanks!

Bill

---

### Post by #&amp;thj^% on 2022-05-28
Good Luck,

---

### Post by Yellow Pasque on 2022-05-30
It might be a bad switch or loose cable: [https://askubuntu.com/questions/891394/wireless-interface-hard-blocked-cannot-bring-up](https://askubuntu.com/questions/891394/wireless-interface-hard-blocked-cannot-bring-up)

---

