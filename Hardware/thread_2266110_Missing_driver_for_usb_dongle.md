---
title: "Missing driver for usb dongle"
date: 2015-02-19
forum: Hardware
---

### Post by jtapp92 on 2015-02-19
Hi, im running LM 17.1 on my  desktop and trying to use a usb dongle, but the driver is not showing up  and the dongle isnt being recognized. dongle is a Realtek WU710N.

after running ```
lsusb
``` i get Bus 001 Device 006: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter

i then followed this link -> [https://sites.google.com/site/easylinux ... /reserve-7]("https://sites.google.com/site/easylinuxtipsproject/reserve-7")

when i run ```
lsmod | grep rtl
``` I get nothing in return

it seems very odd 1. because i can see it recognizes it in lsusb and 2. because its not even showing up in taskbar network settings. :?

also im running kernal 3.13.0-45 i that helps at all.

any help would be greatly appreciated!

---

