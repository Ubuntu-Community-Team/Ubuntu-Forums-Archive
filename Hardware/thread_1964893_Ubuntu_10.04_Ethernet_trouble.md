---
title: "Ubuntu 10.04 Ethernet trouble"
date: 2012-04-24
forum: Hardware
---

### Post by ballzan on 2012-04-24
I just installed ubuntu 10.04 64amd on a Lenovo Thinkstation with an Xeon processor at my college for my independent study class but for some reason it can't find the Ethernet adapter.  I do a ifconfig -a and only the loopback shows up and when I do lspci it shows it there but I can bring any interfaces such as eth0, eth1, ath0 etc up, any suggestions, I have re-installed twice.

---

### Post by wildmanne39 on 2012-04-24
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sanderj on 2012-04-24
> **ballzan said:**
> I just installed ubuntu 10.04 64amd on a Lenovo Thinkstation with an Xeon processor at my college for my independent study class but for some reason it can't find the Ethernet adapter.  I do a ifconfig -a and only the loopback shows up and when I do lspci it shows it there but I can bring any interfaces such as eth0, eth1, ath0 etc up, any suggestions, I have re-installed twice.

Can you live-boot from a Ubuntu 12.04 (beta) CD/USB-stick, and see if it works?

---

### Post by ballzan on 2012-04-24
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

Thanks will try it tomorrow when I get to class.  This isn't a laptop just to verify it is a desktop but this is laptop and hardware and it seems to be a hardware issue thats why its posted here.

---

### Post by ballzan on 2012-04-24
> **sanderj said:**
> Can you live-boot from a Ubuntu 12.04 (beta) CD/USB-stick, and see if it works?

I had ubuntu 11.10 on it before and it worked but my labs require 10.04.

---

### Post by ballzan on 2012-04-25
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
 
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you
 
Here it is.
 
 
```
 
cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS" 
Linux client 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux 


lspci -nnk | grep -iA2 net 
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 05) 
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) 
Kernel driver in use: ehci_hcd 


lsusb 
Bus 002 Device 003: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 04b3:3025 IBM Corp. 
Bus 001 Device 003: ID 17ef:6019 Lenovo 
Bus 001 Device 002: ID 8087:0024 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 


iwconfig 
lo no wireless extensions. 


rfkill list all 


Was blank nothing displayed.


lsmod 
Module Size Used by 
binfmt_misc 6587 1 
ppdev 5259 0 
fbcon 35102 71 
tileblit 2031 1 fbcon 
font 7557 1 fbcon 
bitblit 4707 1 fbcon 
softcursor 1189 1 bitblit 
vga16fb 11385 1 
vgastate 8961 1 vga16fb 
nouveau 467624 0 
ttm 50071 1 nouveau 
drm_kms_helper 29297 1 nouveau 
drm 163143 3 nouveau,ttm,drm_kms_helper 
agpgart 31788 2 ttm,drm 
psmouse 63245 0 
i2c_algo_bit 5028 1 nouveau 
usb_storage 39457 0 
lp 7028 0 
serio_raw 3978 0 
parport 32635 2 ppdev,lp 
usbhid 36174 0 
hid 67032 1 usbhid 
ahci 32040 2 
```

---

### Post by wildmanne39 on 2012-04-25
Hi, let's load the driver and see if it comes on if not post the output from the second command:
```
sudo modprobe e1000e
dmesg | grep e100
```
Thanks

---

### Post by wildmanne39 on 2012-04-25
Hi, I have been doing more research and there is no easy way to get it to work in 10.04 but here is a link where people did get it to work.
[http://ubuntuforums.org/archive/index.php/t-1741686.html](http://ubuntuforums.org/archive/index.php/t-1741686.html)
Thanks

---

### Post by wildmanne39 on 2012-04-25
Hi, I consulted with the resident expert on networking and he recommends this:
```
sudo su
modprobe e1000e
echo "8086 1502" > /sys/bus/pci/drivers/e1000e/new_id
exit
ifconfig
```
Thanks

---

### Post by ballzan on 2012-04-26
> **wildmanne39 said:**
> Hi, I consulted with the resident expert on networking and he recommends this:
```
sudo su
modprobe e1000e
echo "8086 1502" > /sys/bus/pci/drivers/e1000e/new_id
exit
ifconfig
```
Thanks

Okay thanks will do the commands and give you more output, thanks for all the help.

---

