---
title: "LG KU 250 Transfer Files via USB Cable for Internal Memory"
date: 2009-01-24
forum: Hardware
---

### Post by yadhav on 2009-01-24
Hi, guys this is my first thread in Ubuntu Forums. I am an absolute Ubuntu user. I have an LG KU 250 Mobile Phone and I want to Connect it in Ubuntu via USB Cable. Please Help me out guys.:(

Here are a few messages I got:

lsusb

Bus 003 Device 003: ID 1110:9041 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


 dmesg | tail

[ 2954.891545] usbcore: registered new interface driver cdc_acm
[ 2954.892733] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 3003.696056] usb 3-4: USB disconnect, address 4
[ 3006.520035] usb 2-3: new full speed USB device using ohci_hcd and address 2
[ 3006.755478] usb 2-3: configuration #1 chosen from 1 choice
[ 3006.757396] cdc_acm 2-3:1.0: ttyACM0: USB ACM device
[ 3033.456075] usb 2-3: USB disconnect, address 2
[ 3036.489087] usb 2-3: new full speed USB device using ohci_hcd and address 3
[ 3036.716911] usb 2-3: configuration #1 chosen from 1 choice
[ 3036.718744] cdc_acm 2-3:1.0: ttyACM0: USB ACM device

Problem Solved, Am now using Memory Cards :P

---

