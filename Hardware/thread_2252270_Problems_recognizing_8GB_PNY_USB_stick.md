---
title: "Problems recognizing 8GB PNY USB stick"
date: 2014-11-10
forum: Hardware
---

### Post by johnnybrown on 2014-11-10
I'm having issues with my PNY 8GB USB flash drive. When I plug it into my computer, nothing happens. I did some research and was directed to a thread that said to run "*tail -f /var/log/syslog" *and plug the drive. Here is the output I received:

john@JohnsLaptop:~$ tail -f /var/log/syslog
Nov 10 16:08:40 JohnsLaptop kernel: [  768.100416] sd 8:0:0:0: rejecting I/O to offline device
Nov 10 16:08:40 JohnsLaptop kernel: [  768.100422] sd 8:0:0:0: killing request
Nov 10 16:08:40 JohnsLaptop kernel: [  768.216161] usb 2-3: new high-speed USB device number 6 using ehci-pci
Nov 10 16:08:50 JohnsLaptop kernel: [  778.348403] usb 2-3: string descriptor 0 read error: -110
Nov 10 16:08:50 JohnsLaptop kernel: [  778.348419] usb 2-3: New USB device found, idVendor=154b, idProduct=0061
Nov 10 16:08:50 JohnsLaptop kernel: [  778.348424] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 10 16:08:55 JohnsLaptop kernel: [  783.348411] usb 2-3: can't set config #1, error -110
Nov 10 16:08:55 JohnsLaptop mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3"
Nov 10 16:08:55 JohnsLaptop mtp-probe: bus: 2, device: 6 was not an MTP device
Nov 10 16:10:34 JohnsLaptop kernel: [  882.091024] usb 2-3: USB disconnect, device number 6
Nov 10 16:11:22 JohnsLaptop kernel: [  929.864091] usb 2-3: new high-speed USB device number 7 using ehci-pci
Nov 10 16:11:22 JohnsLaptop kernel: [  930.005534] usb 2-3: New USB device found, idVendor=154b, idProduct=0061
Nov 10 16:11:22 JohnsLaptop kernel: [  930.005543] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 10 16:11:22 JohnsLaptop kernel: [  930.005548] usb 2-3: Product: USB 2.0 FD
Nov 10 16:11:22 JohnsLaptop kernel: [  930.005552] usb 2-3: Manufacturer: PNY Technologies
Nov 10 16:11:22 JohnsLaptop kernel: [  930.005557] usb 2-3: SerialNumber: UT2405490000059F
Nov 10 16:11:22 JohnsLaptop kernel: [  930.007013] usb-storage 2-3:1.0: USB Mass Storage device detected
Nov 10 16:11:22 JohnsLaptop kernel: [  930.007272] scsi9 : usb-storage 2-3:1.0
Nov 10 16:11:22 JohnsLaptop mtp-probe: checking bus 2, device 7: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3"
Nov 10 16:11:22 JohnsLaptop mtp-probe: bus: 2, device: 7 was not an MTP device
Nov 10 16:11:44 JohnsLaptop kernel: [  951.952078] usb 2-3: reset high-speed USB device number 7 using ehci-pci
Nov 10 16:11:44 JohnsLaptop kernel: [  952.089261] usb 2-3: can't restore configuration #1 (error=-71)
Nov 10 16:11:44 JohnsLaptop kernel: [  952.089344] usb 2-3: USB disconnect, device number 7
Nov 10 16:11:44 JohnsLaptop kernel: [  952.089446] scsi 9:0:0:0: Device offlined - not ready after error recovery
Nov 10 16:11:44 JohnsLaptop kernel: [  952.204121] usb 2-3: new high-speed USB device number 8 using ehci-pci
Nov 10 16:11:44 JohnsLaptop kernel: [  952.338986] usb 2-3: New USB device found, idVendor=154b, idProduct=0061
Nov 10 16:11:44 JohnsLaptop kernel: [  952.338994] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 10 16:11:44 JohnsLaptop kernel: [  952.338999] usb 2-3: Product: USB 2.0 FD
Nov 10 16:11:44 JohnsLaptop kernel: [  952.339004] usb 2-3: Manufacturer: PNY Technologies
Nov 10 16:11:44 JohnsLaptop kernel: [  952.339008] usb 2-3: SerialNumber: UT2405490000059F
Nov 10 16:11:44 JohnsLaptop kernel: [  952.339480] usb-storage 2-3:1.0: USB Mass Storage device detected
Nov 10 16:11:44 JohnsLaptop kernel: [  952.339597] scsi10 : usb-storage 2-3:1.0
Nov 10 16:11:44 JohnsLaptop mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3"
Nov 10 16:11:44 JohnsLaptop mtp-probe: bus: 2, device: 8 was not an MTP device
Nov 10 16:11:48 JohnsLaptop kernel: [  955.572830] perf samples too long (2505 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Nov 10 16:12:07 JohnsLaptop kernel: [  974.992107] usb 2-3: reset high-speed USB device number 8 using ehci-pci
Nov 10 16:12:07 JohnsLaptop kernel: [  975.244074] usb 2-3: reset high-speed USB device number 8 using ehci-pci
Nov 10 16:12:14 JohnsLaptop kernel: [  981.496062] usb 2-3: reset high-speed USB device number 8 using ehci-pci
Nov 10 16:12:14 JohnsLaptop kernel: [  981.744100] usb 2-3: reset high-speed USB device number 8 using ehci-pci
Nov 10 16:12:14 JohnsLaptop kernel: [  981.996057] usb 2-3: reset high-speed USB device number 8 using ehci-pci
Nov 10 16:12:14 JohnsLaptop kernel: [  982.129139] scsi 10:0:0:0: Device offlined - not ready after error recovery

Obviously, I have some kind of error. This problem started after I was trying to copy an Ubuntu 14.04 ISO to my other system that's running OpenSUSE (HORRIBLE DISTRO BTW) and the copy progress froze at 100%. So I unplugged the USB stick and was going to plug it into my Ubuntu 14.04 machine to format/repartition the drive and create a bootable USB stick so I can put 14.04 on that dreaded SUSE system.

Can somebody please help me out?

---

### Post by houstonbofh on 2014-11-10
Start with lsusb to see if it is seeing the device correctly.  If so, try running gparted, the graphical partition editor.  You will have to hit the dropdown box to go to the correct device as it will default to your boot drive.  If you see it in gparted, you can format it there.

---

### Post by johnnybrown on 2014-11-10
Here is the output of lsusb

john@JohnsLaptop:~$ lsusb
Bus 002 Device 008: ID 154b:0061 PNY 
Bus 002 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

gparted only recognized my hard drive. Basically, I plug in the flash drive and nothing happens.

---

### Post by houstonbofh on 2014-11-12
It is there, but not mounting.  So, I would first try another port and see if it works.  I would also try a LiveCD boot and see if that helps.  The "MPT" in the logs means it is trying to mount it as a camera or tablet, and it shouldn't.

---

