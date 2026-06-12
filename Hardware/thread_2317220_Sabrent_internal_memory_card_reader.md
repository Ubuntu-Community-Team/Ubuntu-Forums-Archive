---
title: "Sabrent internal memory card reader"
date: 2016-03-14
forum: Hardware
---

### Post by shadow of the locust on 2016-03-14
I recently bought a Sabrent internal memory card reader (model: CR-USNT) from Amazon, but it isn't working correctly.

I plugged it into the USB header on the motherboard as per the instructions, and I get the blue power light with no problems.  The usb 2.0 port on the front of the reader works, but none of the card reader slots pick up a card when one is inserted.

My version of Ubuntu is 14.04.4

Results of lsusb are:

> Bus 001 Device 007: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN AdapterBus 001 Device 004: ID 059f:101a LaCie, Ltd 
Bus 001 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 89e5:101b  
Bus 002 Device 003: ID 413c:2111 Dell Computer Corp. 
Bus 002 Device 005: ID 056a:030e Wacom Co., Ltd 
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I was wondering if I have to make any changes to the bios settings to make it work correctly, but I looked and nothing was obviously set wrongly.

If any other information is needed, let me know.

Any help would be greatly appreciated!

Thanks.

---

### Post by sudodus on 2016-03-14
I have used a few card readers, both internal and external, both USB2 and USB3. I have no experience of Sabrent.

All the card readers (that I know) work in linux as well as in Windows as card readers. I have also tried to boot the computer from a card. Some of them work, some don't work. So obviously they are not made according to a common standard.

- Have you tried if your card reader works in Windows?

- Have you checked that the card is good (that it can be used in another card reader or in a camera)?

---

### Post by shadow of the locust on 2016-03-14
Thanks for your reply!

I don't have a windows desktop machine that I can use to test, so I guess that option is out.

Both of the cards (SD and Micro SD) that I have tested are good, and can be read in other computers and devices.

---

### Post by sudodus on 2016-03-14
You can try to return the card reader to Amazon. I guess they would test it in a computer with Windows. Would it be possible for you to borrow a computer with Windows and test it, so that you know what to expect from Amazon.

I don't know the law in your country, but in some countries it is possible to return a product within a couple of weeks after it was delivered, even if it is working, "because you don't like it". In other countries that is not possible.

---

### Post by him610 on 2016-03-15
I have a similar card reader of a different brand that I have had for several years. During a recent rebuild project I installed it as a method of access for SD, XD cards, and the extra USB port. It has 2 LEDs, one for power and one for activity that indicates when some media is installed. The power LED remains illuminated whether the computer is powered or not. The USB port works. The XD media port works. The SD media port does not seem to work, although the Activity LED illuminates. Did not try MS/MS Pro or CF/MD. I have used other Sabrent accessories successfully before.
It is probably a case of hit or miss, and buyer beware.

---

