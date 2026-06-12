---
title: "Battery is quickly discharged, possible cause incorrect vga drivers ?"
date: 2013-03-30
forum: Hardware
---

### Post by JoopGraaf on 2013-03-30
Everything went well on the first sight.
But the battery is very fast empty, and the CPU is working very hard.

So I checked it with powertop. I don't know if this correct but I saw 2 video cards????

  Usage     Device name
            177.1%        CPU use
            100.0%        Audio codec hwC0D3: Intel
            100.0%        Audio codec hwC0D0: IDT
            100.0%        Display backlight
            100.0%        Display backlight
             93.3%        Display backlight
            100.0%        PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1
            100.0%        PCI Device: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
            100.0%        PCI Device: Intel Corporation 3rd Gen Core processor Graphics Controller
            100.0%        PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller
            100.0%        PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1
            100.0%        PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
            100.0%        PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
            100.0%        PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5
            100.0%        PCI Device: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
            100.0%        PCI Device: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
            100.0%        PCI Device: NVIDIA Corporation GK107 [GeForce GT 650M]
            100.0%        PCI Device: Intel Corporation Centrino Wireless-N 2230
            100.0%        Radio device: iwlwifi
            100.0%        USB device: usb-device-8087-07da
            100.0%        USB device: xHCI Host Controller
            100.0%        USB device: EHCI Host Controller
            100.0%        USB device: USB-PS/2 Optical Mouse (Logitech)
            100.0%        USB device: usb-device-8087-0024

So I checked it with lspci and yes there are realy 2 cards???

lion@simson:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 650M] (rev a1)

My question are:
Why are there 2 cards?

Which one is my ubuntu using?

Do I have to install the original driver(NVIDIA-Linux-x86_64-310.40.run) from the Nvidia site?

---

