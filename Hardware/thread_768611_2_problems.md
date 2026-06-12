---
title: "2 problems"
date: 2008-04-26
forum: Hardware
---

### Post by +Synyster on 2008-04-26
my wireless network apapter isn't showing on my network connections list and ubuntu won't let me enable desktop effects

Help please? 

Cheers

---

### Post by overdrank on 2008-04-26
> **+Synyster said:**
> my wireless network apapter isn't showing on my network connections list and ubuntu won't let me enable desktop effects

Help please? 

Cheers

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by +Synyster on 2008-04-26
> **overdrank said:**
> Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

my result:

> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b


---

### Post by overdrank on 2008-04-26
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
Is the graphics card and if you are running Hardy I cannot help with the desktop effects

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b 
Wireless adapter and this has been a issue
[http://ubuntuforums.org/showthread.php?t=766804&highlight=Cisco+Aironet+Wireless+802.11b](http://ubuntuforums.org/showthread.php?t=766804&highlight=Cisco+Aironet+Wireless+802.11b)

---

### Post by +Synyster on 2008-04-26
> **overdrank said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
Is the graphics card and if you are running Hardy I cannot help with the desktop effects

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b 
Wireless adapter and this has been a issue
[http://ubuntuforums.org/showthread.php?t=766804&highlight=Cisco+Aironet+Wireless+802.11b](http://ubuntuforums.org/showthread.php?t=766804&highlight=Cisco+Aironet+Wireless+802.11b)

i was doing some digging and found out that if i add SKIP_CHECKS=yes to the compiz config file it will work but it wont let me save because of permissions. How do i save it?

---

### Post by overdrank on 2008-04-26
> **+Synyster said:**
> i was doing some digging and found out that if i add SKIP_CHECKS=yes to the compiz config file it will work but it wont let me save because of permissions. How do i save it?

Are you opening the file as root? Can you post the link to the instructions?

---

### Post by +Synyster on 2008-04-26
erm I don't think so. I'm a total noob to Linux. 

Erm can't find the link I just searched ubuntu driver for radeon mobility 7500 it was the 1st link

---

### Post by +Synyster on 2008-04-26
ah found it

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330)

---

### Post by overdrank on 2008-04-26
> **+Synyster said:**
> ah found it

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330)
Ok then you can use this command 
Example ```
gksudo gedit /etc/xdg/compiz/compiz-manager
```
I also believe that the gksudo gedit will work with your wireless bug fix also.

---

### Post by +Synyster on 2008-04-26
wow after rebooting it fixed my sound aswell as my wireless

---

### Post by +Synyster on 2008-04-26
Uh oh my computer crashes now when I try to connect to a wireless network

---

### Post by overdrank on 2008-04-26
> **+Synyster said:**
> Uh oh my computer crashes now when I try to connect to a wireless network

HI and there was two possible fixes you can try both but only one at a time. Be sure to undo the first.

---

### Post by +Synyster on 2008-04-26
what are they?

---

### Post by overdrank on 2008-04-26
> **+Synyster said:**
> what are they?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398)

---

### Post by +Synyster on 2008-04-26
I think I'll make it less complicated for myself and install 7.10 instead

---

### Post by +Synyster on 2008-04-26
what does it mean when it says "commented out the first 2 occurances of aes that link to padlock and geode hardware"?

---

### Post by overdrank on 2008-04-26
> **+Synyster said:**
> what does it mean when it says "commented out the first 2 occurances of aes that link to padlock and geode hardware"?

Hi and when you edit the file you will place a # in front of the line

---

### Post by +Synyster on 2008-04-26
Thanks for that but still neither of the fixes work. My computer still freezes when connecting to a wireless network

---

### Post by overdrank on 2008-04-26
> **+Synyster said:**
> Thanks for that but still neither of the fixes work. My computer still freezes when connecting to a wireless network

I am sorry I am by no means a wireless expert but a quick search may help
[http://ubuntuforums.org/search.php?searchid=39971129](http://ubuntuforums.org/search.php?searchid=39971129)

---

