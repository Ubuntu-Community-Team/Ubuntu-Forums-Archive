---
title: "USB Ports Stopped Working"
date: 2017-04-22
forum: Hardware
---

### Post by tolgakacmaz on 2017-04-22
I have Ubuntu 16.04.2 LTS installed on my pc. (64bit) One usb port had been disabled several weeks ago, but i didnt care much  because still 2 avaliable usbs, but the other one stopped working also.

 Linux version 4.10.12-041012-lowlatency (kernel@gloin) (gcc version 6.2.0 20161005 (Ubuntu 6.2.0-5ubuntu12) ) #201704210512 SMP PREEMPT Fri Apr 21 09:17:26 UTC 2017

  I've tried;

  [USB ports have completely stopped working]("https://askubuntu.com/questions/824454/usb-ports-have-completely-stopped-working")
  [2 usb ports stopped working]("https://askubuntu.com/questions/526082/2-usb-ports-stopped-working")
  [USB slots stop working suddenly from time to time]("https://askubuntu.com/questions/206614/usb-slots-stop-working-suddenly-from-time-to-time")
  [Laptop USB ports stop working: how to restart them without restarting the PC?]("https://askubuntu.com/questions/178054/laptop-usb-ports-stop-working-how-to-restart-them-without-restarting-the-pc")

  these solutions but none of them works. 

Right now, 1 USB doesnt work completely. When i plug a device to other  one, it only charges the device. (i tried with android phone, kindle,  external hdd, flashdisk)


  My grub file have these lines;
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi=force irqpoll usbcore.autosuspend=-1"
GRUB_CMDLINE_LINUX="acpi=force irqpoll"

  These results are when phone is connected but only charging ;

  ```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 04f2:b50e Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 046d:c246 Logitech, Inc. Gaming Mouse G300
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 1: Dev 6, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 1: Dev 6, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 4: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
    |__ Port 4: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 5: Dev 4, If 0, Class=Vendor Specific Class, Driver=rtsx_usb, 480M
    |__ Port 7: Dev 5, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 7: Dev 5, If 1, Class=Wireless, Driver=btusb, 12M

ls /sys/bus/pci/drivers/
agpgart-intel  ehci-pci       iwlwifi     r8169      uhci_hcd
agpgart-via    i915       mei_me      radeon         virtio-pci
ahci           imsttfb        ohci-pci    serial         xen-platform-pci
asiliantfb     intel_pch_thermal  parport_pc  shpchp         xhci_hcd
ata_generic    intel_pmc_core     pata_sis    snd_hda_intel
ata_piix       iosf_mbi_pci   pcieport    snd_soc_skl

ls /sys/bus/pci/drivers/xhci_hcd/
0000:00:14.0  bind  new_id  remove_id  uevent  unbind

```

 When i unbind 0000:00:14.0, mouse stops working (the only working usb)


  dmesg log is here : [https://pastebin.com/is0GgmKk](https://pastebin.com/is0GgmKk)
dmesg | grep USB : [https://pastebin.com/D0L9f2nt](https://pastebin.com/D0L9f2nt)
  usb-devices result : [https://pastebin.com/Zg1hHRtN](https://pastebin.com/Zg1hHRtN)
[LEFT][COLOR=#333333][FONT=Consolas]lspci and cat /proc/bus/input/devices : [https://pastebin.com/iEerB9Wu](https://pastebin.com/iEerB9Wu)
[/FONT][/COLOR][/LEFT]

---

### Post by tolgakacmaz on 2017-04-22
i updated xorg and kernel, not dmesg | grep usb  is like this ; [https://pastebin.com/3VkTgyEC](https://pastebin.com/3VkTgyEC)

and the issuas are the same. one of the usb ports is dead, the other is only charging, one (with mouse plugged) is working. 

i found this : [https://unix.stackexchange.com/questions/323692/what-does-usb-port-power-management-may-be-unreliable-actually-mean](https://unix.stackexchange.com/questions/323692/what-does-usb-port-power-management-may-be-unreliable-actually-mean)
for dmesg '[LEFT][COLOR=#333333][FONT=Consolas]usb: port power management may be unreliable', but it doesnt provide any answers[/FONT][/COLOR][/LEFT]

---

