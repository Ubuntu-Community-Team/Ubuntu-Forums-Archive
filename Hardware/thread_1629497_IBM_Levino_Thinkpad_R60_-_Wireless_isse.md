---
title: "IBM Levino Thinkpad R60 - Wireless isse"
date: 2010-11-23
forum: Hardware
---

### Post by revelation2012 on 2010-11-23
Hello. I am new to Ubuntu and Linix and need a little help having my **Levino IBM ThinkPad R60** recognize the onboard wirless card. You've no doubt heard that before . . . .
 
I thought I would be thrifty and try to wipe the pathetically slow MS XP OS on this machine and load Ubuntu 10.04.1 on this decomissined laptop from my business. Well it workd fine and but I am having a terrible time with the wlan0 interface. I followed a thread with the same card (listed below) and got it operational but after a reboot it again did not recognize the card. I have since gone through the thread again and cannot connect the card again. This was the thread I was using to configre the card but I have now given up (for the time being) and amd posting my own thread to get help. 
 
Could anyone give a step by step command to get this wireless card recognized. And for that matter for me to be able to reboot the Laptop and have it still recognize the wireless card and locate access points. I appreciate any help. Below is the onboard wirless card specs:
 
> 
*-network DISABLED 
description: Wireless interface 
product: PRO/Wireless 3945ABG [Golan] Network Connection 
vendor: Intel Corporation 
physical id: 0 
bus info: pci@0000:03:00.0 
logical name: wlan0 
version: 02 
serial: 00:13:02:c7:dd:f4 
width: 32 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg 
resources: irq:32 memory:edf00000-edf00fff 

 
Thanks
 
Edit: Sorry, here was the thread I was trying to follow and had success once until I rebooted:
[http://art.ubuntuforums.org/showthread.php?t=1096752](http://art.ubuntuforums.org/showthread.php?t=1096752)

---

### Post by revelation2012 on 2010-11-24
I am preiodically able to get the wirless card to be recongnized with the following command:
 
> sudo modprobe iwl3945
ifconfig
 
Then I will run this anmd it shows connected:
 
> sudo lshw -C netwok

 
I then will reboot and it loses the card again. An no matter what I do I cannot get it to activate again. So I must be doing something that is causing it to disable but I am not well versed eough in unix/linux/ubuntu to understand what I did wrong.
 
I downlaoeded Wicd and it seems to recognize the access poins but the traditoninal connection software in Ubuntu shows disabled even though the networking and wirless are checked as enabled.
 
Appreciate any guidance as this is frustrating.

---

### Post by revelation2012 on 2010-11-24
Okay. I am getting a little further . . . I can consitantly bring up the wlan0 with the following commands.
 
> sudo modprobe iwl3945
ifconfig
 
How can I get Ubuntu to have these active after a reboot?

---

### Post by Fafler on 2010-11-25
The ifconfig command itself does nothing except listing the available network interfaces.

To make sure you modprobe the iwl3945 driver at boot, do a
```
echo iwl3945 | sudo tee -a /etc/modules
```

---

### Post by revelation2012 on 2010-11-25
Fafler:

On this day of Thanksgiving I am very thankful for your reply. the command worked perfectly. After execution of the command you provided, I rebooted and the wireless popped up right away. Thanks brother you are the best!:D

Rich

---

### Post by Fafler on 2010-11-26
You're welcome. Didn't even know it was thanksgiving. We don't really celebrate that on my side of the pond.

---

