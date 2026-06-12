---
title: "USB Genius HS-210U, Ubuntu 14.04"
date: 2016-05-11
forum: Hardware
---

### Post by jyolotin on 2016-05-11
Hello,  I have usb headset Genius HS-210U (new)  

my diagnostic output:  

$ uname -r 
4.2.0-35-generic  

$ lsusb 

Bus 001 Device 003: ID 0c76:160b JMTek, LLC. 

  dmesq: 
dmesg | grep '1-1.2' 
[    1.564390] usb 1-1.2: new full-speed USB device number 3 using ehci-pci 
[    1.657322] usb 1-1.2: New USB device found, idVendor=0c76, idProduct=160b 
[    1.657326] usb 1-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0 
[    1.657329] usb 1-1.2: Product: USB Audio Device 
[    2.789798] input: USB Audio Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.3/0003:0C76:160B.0001/input/input5 

 no error in dmesq (if need i can show total output)  

alsamixer and pavucontrol didn't see usb headset: 
default 
0 HDA Intel PCH 
1 HDA Invidia 
....   $ 

cat /proc/asound/cards:  
0 [PCH            ]: HDA-Intel - HDA Intel PCH                       HDA Intel PCH at 0xf7100000 irq 27  
1 [NVidia         ]: HDA-Intel - HDA NVidia                       HDA NVidia at 0xf7080000 irq 17 

 in some instruction i set in: 

$ sudo vi /etc/modprobe.d/alsa-base.conf 
options snd-usb-audio index=1  

lspci: 
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09) 
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) 
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) 
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) 
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) 
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) 
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05) 
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05) 
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
 00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05) 
01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 730] (rev a1) 
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1) 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06) 

 Please, help me to make it work. What i must do? I read many posts and topics and i can't find proper whay to make it work. And I can't reinstall ubuntu because have my user's information in it.

---

