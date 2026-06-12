---
title: "Suddenly, my USB Keyboard and Mouse not works"
date: 2009-12-27
forum: Hardware
---

### Post by ZardoZ84 on 2009-12-27
Happy X-Mas!
I 'm working wich Ubuntu/Kubuntu from some years ago. Yesterdey, wichout install anything or updating anything, my USB keyboard and mouse stoped to work wich Ubuntu (even the LEDs of the keyboard and mice shutoff!!!). I not have idea why!

In windows they works fine, and the more extrange thing is that in a LIVE USB of Kubuntu Karmic I get the same problem!
But I discover that if I wait around  of 3 minutes in the login screen, the keyboard and mouse begin to work.
I think that perhaps is a problem wich the USB controler of my motherboard.



lsusb:

```
Bus 002 Device 009: ID 04b4:0033 Cypress Semiconductor Corp.
Bus 002 Device 008: ID 0b38:0003
Bus 002 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 002: ID 03f0:3c02 Hewlett-Packard PhotoSmart 7350
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


dmesg:
```
                                    
[   16.512030] usb 1-7: device descriptor read/64, error -110                                                                                     
                                                                                     
[   31.728029] usb 1-7: device descriptor read/64, error -110                                                                                     
[   31.944026] usb 1-7: new high speed USB device using ehci_hcd and address 5                                                                    
[   31.967980] type=1503 audit(1261865713.539:35): operation="open" pid=1677 parent=1676 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"                                                                                           
[   32.976116] type=1503 audit(1261865714.551:36): operation="open" pid=1687 parent=1686 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"                                                                                           
[   33.984821] type=1503 audit(1261865715.559:37): operation="open" pid=1697 parent=1696 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"                                                                                           
[   34.992227] type=1503 audit(1261865716.567:38): operation="open" pid=1707 parent=1706 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"                                                                                           
[   36.001620] type=1503 audit(1261865717.575:39): operation="open" pid=1717 parent=1716 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"                                                                                           
[   36.009916] type=1503 audit(1261865717.583:40): operation="open" pid=1726 parent=1725 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"                                                                                           
[   36.539490] vboxdrv: Trying to deactivate the NMI watchdog permanently...                                                                      
[   36.539494] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance                                                   
[   36.539495] vboxdrv: counter framework which can generate NMIs is active. You have to prevent                                                  
[   36.539497] vboxdrv: the usage of hardware performance counters by                                                                             
[   36.539497] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid                                                                         
[   36.539501] vboxdrv: Found 2 processor cores.                                                                                                  
[   36.539566] vboxdrv: fAsync=1 offMin=0x14633f offMax=0x14633f                                                                                  
[   36.539603] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.                                                                
[   36.539605] vboxdrv: Successfully loaded version 3.0.10 (interface 0x000e0001).                                                                
[   37.473018] eth0: no IPv6 routers present                                                                                                      
[   47.056028] usb 1-7: device descriptor read/64, error -110                                                                                     
[   62.272029] usb 1-7: device descriptor read/64, error -110                                                                                     
[   62.488026] usb 1-7: new high speed USB device using ehci_hcd and address 6                                                                    
[   67.508103] usb 1-7: device descriptor read/8, error -110                                                                                      
[   72.628110] usb 1-7: device descriptor read/8, error -110                                                                                      
[   72.844027] usb 1-7: new high speed USB device using ehci_hcd and address 7                                                                    
[   77.864107] usb 1-7: device descriptor read/8, error -110                                                                                      
[   82.984110] usb 1-7: device descriptor read/8, error -110                                                                                      
[   83.088032] hub 1-0:1.0: unable to enumerate USB device on port 7                                                                              
[   83.544026] usb 2-1: new full speed USB device using ohci_hcd and address 2                                                                    
[   83.768160] usb 2-1: configuration #1 chosen from 1 choice                                                                                     
[   83.783132] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3C02                                                   
[   83.783148] usbcore: registered new interface driver usblp                                                                                     
[   84.072027] usb 2-4: new full speed USB device using ohci_hcd and address 3                                                                    
[   84.284159] usb 2-4: configuration #1 chosen from 1 choice                                                                                     
[   84.288087] hub 2-4:1.0: USB hub found                                                                                                         
[   84.290091] hub 2-4:1.0: 4 ports detected
[   84.608025] usb 2-7: new full speed USB device using ohci_hcd and address 4
[   97.292028] Clocksource tsc unstable (delta = -87485842 ns)
[   99.784036] usb 2-7: device descriptor read/64, error -110
[  115.064040] usb 2-7: device descriptor read/64, error -110
[  115.344040] usb 2-7: new full speed USB device using ohci_hcd and address 5
[  130.520040] usb 2-7: device descriptor read/64, error -110
[  145.800041] usb 2-7: device descriptor read/64, error -110
[  146.080037] usb 2-7: new full speed USB device using ohci_hcd and address 6
[  151.100125] usb 2-7: device descriptor read/8, error -110
[  156.220126] usb 2-7: device descriptor read/8, error -110
[  156.500037] usb 2-7: new full speed USB device using ohci_hcd and address 7
[  166.908036] usb 2-7: device not accepting address 7, error -110
[  166.908056] hub 2-0:1.0: unable to enumerate USB device on port 7
[  166.986123] usb 2-4.1: new low speed USB device using ohci_hcd and address 8
[  167.095300] usb 2-4.1: configuration #1 chosen from 1 choice
[  167.144008] usbcore: registered new interface driver hiddev
[  167.150766] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.1/2-4.1:1.0/input/input4
[  167.150917] generic-usb 0003:0B38:0003.0001: input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:0b.0-4.1/input0
[  167.161313] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.1/2-4.1:1.1/input/input5
[  167.161547] generic-usb 0003:0B38:0003.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:0b.0-4.1/input1
[  167.161586] usbcore: registered new interface driver usbhid
[  167.161593] usbhid: v2.6:USB HID core driver
[  167.182218] usb 2-4.2: new low speed USB device using ohci_hcd and address 9
[  167.294311] usb 2-4.2: configuration #1 chosen from 1 choice
[  167.308701] input: HID 04b4:0033 as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.2/2-4.2:1.0/input/input6
[  167.308888] generic-usb 0003:04B4:0033.0003: input,hidraw2: USB HID v1.00 Mouse [HID 04b4:0033] on usb-0000:00:0b.0-4.2/input0
[  168.344492] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
```

---

### Post by mahdiyeh on 2010-01-31
Hello
 
I am worg in ubuntu 8.4 on dell vostro 1520 laptop and i have the sam problem too, suddenlly my keyboard and touchpad does not work but windows has no problem with it!!! 
I need a solution except reinstallation!!
did anyidea?
 
[email]s.bakhshaei@yahoo.com[/email]

---

