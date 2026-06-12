---
title: "wlan BCM4328 without ndiswrapper"
date: 2008-05-18
forum: Hardware
---

### Post by wette on 2008-05-18
Hi everybody,

Im running Linux on my Macbook 3.1.
it has the wlan card
Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
buildin
But im wondering about my battery consumption.
the ndiswrapper seems not to be able to handle the chip in a battery-friendly way.

so is it possible to use another module then ndiswrapper for the BCM4328?

- wette

---

### Post by brujoand on 2008-05-18
bcm43xx should work.. 

You can swap with

   sudo rmmod ndiswrapper
   sudo modprobe bcm43xx

Works on my old laptop with 7.10. 
Good performance to

---

### Post by wette on 2008-05-18
Hey,
if doing so (but i have b43 and not bcm43xx)
i get:
Broadcom 43xx driver loaded [ Features: PMLR, Firmware-ID: FW13 ]
in my /var/log/messages

but no wlan device is displayer using ifconfig.

do i have the wrong firmware version ?

- wette

---

### Post by brujoand on 2008-05-18
hm.. thats odd. The bcm43xx should have come with the kernel headers.. I'm not familier with the b43, so i can't tell you why that's not working.

What does iwconfig give you?

---

### Post by wette on 2008-05-18
b43 should be the same as bcm43xx

but: are you sure that you have a BCM4328 chipset?

because 5 minutes ago i read on linuxwireless that there is no support for BCM4328 in the drivers.

i think i do not have bcm43xx driver because actually i am not using ubuntu but fedora..

iwconfig only shoes up my local loopback und my wired-lan beeing no wlan-cards.

- wette

---

### Post by brujoand on 2008-05-18
> because 5 minutes ago i read on linuxwireless that there is no support for BCM4328 in the drivers.

Ahh..  my bad, I read the numbers wrong.
I guess your stuck with ndiswrapper untill someone blackboxes the driver or broadcom start treating there customers with due respect. I spent my first 6 months in the linuxworld getting my broadcom card working, so I know how you feel.

Good luck to you :)

---

