---
title: "Cannot stop fan in Ubuntu 13.10"
date: 2014-01-05
forum: Hardware
---

### Post by 3.142 on 2014-01-05
I ave an Acer Aspire R7, running a dual boot of Ubuntu 13.10 and Windows 8. 
My fan now runs nonstop after booting the computer, and I have tried every suggested solution I could find,
but none of them have helped. 
I tried lm-sensors and fancontrol, but pwmconfig does not detect any sensors for the fan. 
The fan is running nonstop and it's driving me crazy!
Has anybody confronted and defeated this problem without fancontrol?
 Any possible alternative solutions would be much appreciated!

---

### Post by QIII on 2014-01-06
Hello!

Could you post the hardware specs of that machine?

---

### Post by 3.142 on 2014-01-06
Hi! It is a laptop with 6 GB RAM, an Intel i5 CPU, and with Intel IvyBridge graphics. 
Is there anything else necessary?

---

### Post by Yellow Pasque on 2014-01-06
Make sure BIOS is up to date. I see there are some BIOS updates for certain models of R7. Do they fix any fan control issues? Your guess is as good as mine since Acer's BIOS team seems to be more allergic to changelogs than AMD's Linux Catalyst team has been for the better part of the last 5 years...

---

### Post by 3.142 on 2014-01-06
Thanks for your reply and for your time; I have actually updated the BIOS earlier today, and there were no changes made that helped with fan control.

---

### Post by QIII on 2014-01-06
So this starts at boot, through POST and persists into loading both Windows and Ubuntu?

---

### Post by 3.142 on 2014-01-06
Yes, the fan persists in both Windows in Ubuntu. Though it stops for long periods(maybe of a few minutes) sometimes in Windows, but not in Ubuntu.
The problem began after the installation of Ubuntu.

---

### Post by Yellow Pasque on 2014-01-06
Tried resetting BIOS to defaults?

---

### Post by 3.142 on 2014-01-06
There aren't many options in the BIOS, just boot order, admin password, legacy/uefi boot;
I searched for something that might refer to fans, but there is nothing. 
There is an option to boot with defaults, which I've tried and which does not fix the problem.
(I might note that default is to use UEFI, which boots windows, but I have to switch to legacy 
boot for ubuntu.)

---

