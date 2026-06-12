---
title: "Webcam not working"
date: 2008-11-20
forum: Hardware
---

### Post by rajendrag on 2008-11-20
Hi,

I am newbie to Ubuntu. After toiling for days i have managed to make my laptop (toshiba qosmio f10) dual bootable with Ubuntu hardy and windows xp. I would like to make a complete switch over to Ubuntu but there is one problem. Ubuntu is not detecting Hytech webcam. I have tried the help available within the forum but without any success. Can anyone help me to fix the webcam problem?

Here is the result of lsusb.

#lsusb  

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0c45:6128 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Many thanks,

Raj  :)

---

### Post by sjbaugh on 2008-11-20
The Microdia is a webcam device. On Linux these things are often refered to by the chipset they use rather than the manufacturers designation. You might try to install cheese from the repository to see if it is working. Other than that I am not a webcam expert.

Steve

---

### Post by rajendrag on 2008-11-20
> **sjbaugh said:**
> The Microdia is a webcam device. On Linux these things are often refered to by the chipset they use rather than the manufacturers designation. You might try to install cheese from the repository to see if it is working. Other than that I am not a webcam expert.

Steve
I have tried Cheese still webcam refuses to work.

---

### Post by sjbaugh on 2008-11-21
Raj,

First see the webcam issues in:

[http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)


If that does not work, I have just fixed my webcam problems with the help of a bug report at:

[https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

It is rather a complicated fix and you will have to see if it will work with your particular webcam.

Steve

---

### Post by rajendrag on 2008-11-21
Whether the webcam issues are relevant to Ubuntu 8.04 that i am using? Can you please give some more information on how did you solve the webcam problem with the help of bug report?

Thanks,

Raj

---

### Post by sjbaugh on 2008-11-21
Raj,

Even though you said it, I missed the "hardy" in your first quote, sorry. You are right that what I said was not relevant. The conculsion would seem to be that the 0c45:6128 Microdia webcam is not supported in the 8.04 gspca driver, the "built-in" webcam driver. I cannot find it in the support list for this driver. 

An internet search for something like "0c45:6128 Microdia Linux Driver" might find a way to use it, it throws up quite a few hits.

Sorry about the confusion,

Steve

---

### Post by jfraire on 2008-11-21
Actually, the driver should be the sn9cxxx, where the 'x' stand for a number. Try the command dmesg to see if the driver is loaded (or what driver is loaded) after you connect the camera to your system.

---

### Post by rajendrag on 2008-11-22
dmesg command does not give any information about the kind of driver loaded. Instead i get several lines of output similar to the following ones:

0 SRC=147.143.242.148 DST=255.255.255.255 LEN=76 TOS=0x00 PREC=0x00 TTL=128 ID=11149 PROTO=UDP SPT=1004 DPT=1004 LEN=56 
[ 3844.754642] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:03:0d:96:ec:c3:08:00 SRC=147.143.242.148 DST=255.255.255.255 LEN=68 TOS=0x00 PREC=0x00 TTL=128 ID=11150 PROTO=UDP SPT=1004 DPT=1004 LEN=48 
[ 3845.485564] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1f:16:04:f8:31:08:00 SRC=147.143.242.221 DST=147.143.242.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=14934 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3846.219709] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1f:16:04:f8:31:08:00 SRC=147.143.242.221 DST=147.143.242.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=14992 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 3846.308790] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:25:13:6a:a1:08:00 SRC=147.143.242.164 DST=147.143.242.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=21279 PROTO=UDP SPT=138 DPT=138 LEN=209 
[10918.806785] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:15:22:8f:6d:08:00 SRC=147.143.242.192 DST=255.255.255.255 LEN=77 TOS=0x00 PREC=0x00 TTL=64 ID=12238 PROTO=UDP SPT=1004 DPT=1004 LEN=57 
[10924.283502] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:03:0d:96:ec:c3:08:00 SRC=147.143.242.148 DST=255.255.255.255 LEN=76 TOS=0x00 PREC=0x00

Can anyone suggest the way out??

---

