---
title: "Camera will not work after latest update (today) on my Samsung laptop"
date: 2021-03-02
forum: Hardware
---

### Post by fabiocanedo on 2021-03-02
Hi, I have a samsung laptop and after today's update my built-in webcamera stopped working.

Here is some output:

```
sudo lshw | grep -C 10 -i "usb"
```

```

       serial: 123490EN400015
       slot: Middle
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P03REP.034.181016.ZW
          date: 10/16/2018
          size: 64KiB
          capacity: 16MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0,5 ns)
             product: HTH5AN8G6NAFR-UHD
             vendor: Hitachi
             physical id: 0
--
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 08
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:f7120000-f7127fff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:125 memory:f7110000-f711ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.4.0-66-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: HP 1000 USB Optical Mouse
                   vendor: PixArt
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1
                   description: Keyboard
                   product: CASUE USB KB
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:2
                   description: Mouse
                   product: CTL-472
                   vendor: Wacom Co.,Ltd.
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.00
                   serial: 0GE00L1002064
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=498mA speed=12Mbit/s
              *-usb:3
                   description: Bluetooth wireless interface
                   vendor: Qualcomm Atheros Communications
                   physical id: 5
                   bus info: usb@1:5
                   version: 0.01
                   capabilities: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.4.0-66-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz

```

And also:

```
 sudo neofetch 
```

```

            .-/+oossssoo+/-.               root@fabio-340XAA-350XAA-550XAA 
        `:+ssssssssssssssssss+:`           ------------------------------- 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 20.04.2 LTS x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: 340XAA/350XAA/550XAA P03REP 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 5.4.0-66-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 48 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 3989 (dpkg), 19 (snap) 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 5.0.17 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1366x768 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: Mutter 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM Theme: Adwaita 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Theme: Adwaita [GTK3] 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Icons: Adwaita [GTK3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Terminal: gnome-terminal 
  +sssssssssdmydMMMMMMMMddddyssssssss+     CPU: Intel i5-8250U (8) @ 3.400GHz 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      GPU: Intel UHD Graphics 620 
    .ossssssssssssssssssdMMMNysssso.       GPU: NVIDIA GeForce MX110 
      -+sssssssssssssssssyyyssss+-         Memory: 3352MiB / 7871MiB 
        `:+ssssssssssssssssss+:`
            .-/+oossssoo+/-.                                       
                                                                   




```

I also should point out that the output to:


```
sudo lshw | grep -C 10 -i "camera"
```

is empty.

---

### Post by him610 on 2021-03-04
Are not most laptop cameras on the USB bus? 
Does this show any?
```

sudo lshw | grep -C 10 -i "webcam"

```

or
```

sudo lshw | grep -C 10 -i "cam"

```

---

### Post by fabiocanedo on 2021-03-05
> **him610 said:**
> Are not most laptop cameras on the USB bus? 
Does this show any?
```

sudo lshw | grep -C 10 -i "webcam"

```

or
```

sudo lshw | grep -C 10 -i "cam"

```

The output to both of these was empty.

---

### Post by fabiocanedo on 2021-03-10
It magically solved itself after a couple of days looking for stuff on the forums.
I just restarted the computer, and it worked. I had done it before, but it didn't work until now.
I don't really know what happened, if anyone know what logs would be useful to post here, I'd really appreciate it if someone told me. So this post can help the community.

---

