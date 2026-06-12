---
title: "Sony Ericsson P800 GPRS"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Samsa on 2005-04-12
I am using from some week Ubuntu with greatest satisfaction. My old DELL Inspiron 3800 has not had problems to recognize the Xircom PC card. Instead, I do not succeed to use a cellular telephone [COLOR=DarkRed]Sony Ericsson P800 [/COLOR] with a cable [COLOR=DarkRed]USB Dcu-11[/COLOR]. I have used pppconfig but without success. Online is a good documentation (as an example here --> [http://mobile.linux.pt/p800](http://mobile.linux.pt/p800)), but I am a neophyte with Linux. What is the way to say Ubuntu that the Sony Ericsson P800 is at the USB port?

---

### Post by kalmisto on 2005-05-13
[QUOTE=Samsa]What is the way to say Ubuntu that the Sony Ericsson P800 is at the USB port?[/QUOTE]

You can find USB-ports from /dev/sda* or if you have sata-drives, propably /dev/sdb*. Use fdisk or something to see if theres something on the other end. (for example fdisk /dev/sda) Hope this answers to some part of your question.

---

### Post by kalmisto on 2005-05-25
Again I was wrong, the easiest way to find out where your phone is connected via usb-cable is to 'tail /var/log/messages'. 

I got this:
May 25 10:17:16 localhost kernel: usb 4-2: PL-2303 converter now attached to ttyUSB0

That means my phone is connected to /dev/ttyUSB0

---

