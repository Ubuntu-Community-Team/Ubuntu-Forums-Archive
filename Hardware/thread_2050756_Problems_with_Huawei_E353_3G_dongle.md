---
title: "Problems with Huawei E353 3G dongle"
date: 2012-08-31
forum: Hardware
---

### Post by Flarp on 2012-08-31
Hello,

i have a little problem Huawei E353 3G modem usb dongle. I'm using Ubuntu 12.04 32-bit on my laptop and i read that 12.04 should support that modem out-of-box. Apparently the truth isn't that nice.

I assume the problem  is with the device's product identifier number (PID). Kernel module called "option" try to find device with VID 0x12D1 and PID 0x1506, but because my dongle is branded by an operation the PID has been changed to 0x151A. I assume its still same device tho.

So i guess that i have to make an alias for the device, but is this any way possible without recompiling option.ko? I got plenty of aliases for devices with "modinfo option", but i have no clue how to configure it. I appreciate if someone would point me to the right direction to solve this issue.

---

### Post by dgharmon on 2012-08-31
> **Flarp said:**
> Hello, i have a little problem Huawei E353 3G modem usb dongle

This might help ...

[usb_modeswitch with Huawei e220]("http://www.linuxquestions.org/questions/linux-software-2/usb_modeswitch-with-huawei-e220-842712/")

---

### Post by pdc on 2012-09-01
> dmesg | grep tty

copy and paste that into a terminal

if you get tty0 you should be able to use the modem;

if not, install usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by Flarp on 2012-09-02
Thanks for the responses. I somewhat solved this issue.

I made following configuration file for usb_modeswitch:
```
# HUAWEI E353 (DNA)

DefaultVendor=0x12d1
DefaultProduct=0x151a
TargetVendor=0x12d1
TargetProduct=0x14ac

MessageContent="55534243123456780000000000000a11062000000000000100000000000000"
```Run with command "**sudo usb_modeswitch -c huawei_e353.conf**" or whatever your filename is. Voila! New usb device with VID 0x12D1 and PID 0x14AC discovered and identified as 3G-modem.

Apparently I have to run this command every time when I plug dongle into the computer. I removed DefaultVendor and DefaultVendor lines form the file and renamed it to "12d1:151a" and put it into folder "/etc/usb_modeswitch.d/" but it doesn't really do anything. Is this location deprecated for custom configs? I'm running usb_modeswitch 1.2.3

---

### Post by BennyRock on 2012-09-07
Thank you Flarp, you made it! 

Did not find any other solution on the internet than this for Finnish DNA ISP:s Huawei E353!

Seen in forums that other ISP:s (Saunalahti, Sonera) Huawei E353 should work out of the box in 12.04. That is certanly not the case for DNA E353.

Worked flawlessly on Xubuntu 12.04 on my friends very old laptop (Intel Pentium M, does not even support pae, thats why Xubuntu 12.04)

---

