---
title: "Xubuntu: USB 3D printer device is not showing up in /dev."
date: 2015-02-03
forum: Hardware
---

### Post by landstander on 2015-02-03
**_System Specifications:_**
**OS:** Xubuntu 14.04
**Motherboard:** ASUS P5E3 Delux WiFi-Ap@n (with latest and last firmware released)
**USB Specs:** USB v2.0 (If I'm not mistaken this motherboard may have been released before the USB 3.0 standard came out)
**3D printer:** Printrbot Simple (1405) (...and yes, Printrbot is spelled without the _e_ as in Print_e_rbot)

**_Description of problem (with more detail):_**
For a short while the Printrbot Simple was found at /dev/ttyACM0 when it was plugged into the computer. Now the printrbot does not show up under /dev at all when the printr is plugged in not even after rebooting the computer. **Note:** This doesn't happen with a regular USB thumb drive. If I unmount a thumbdrive and physically unplug it, that thumbdrive disappears under "/dev", but once that thumbdrive is physically plugged back in, that thumbdrive automatically shows up again as "/dev/sdd1".

**_Things I have tried:_**
[LIST=1]
[*] Using multiple advanced search terms on ubuntuforums.org for this issue with the Xubuntu prefix returned no results.
[*] Searching the web and other forums also returned no results.
[*] I have tried multiple USB cables to rule out a bad cable testing with another device both before and after the 3D printer was plugged in to make sure the cable works.
[*] I have made sure the USB cable is seated properly on both ends for a good physical connection, and I have inspected the circuit boards on both ends to make sure the solder joints connecting the USB sockets had not developed a crack or a break, and both ends look very good and like new with no signs of physical breakage.
[*] I have tried plugging in at different USB ports on the computer.
[*] I have also checked to make sure the power on the printer was on after it was disconnected from the computer and reconnected to it. This procedure has also been repeated by power cycling the printer between unplugging and plugging it back in to rule out any power issues with the printer.
[*] After a fresh start of the computer, the printer's power is plugged in, then the printer is plugged into the computer, it does not show up in /dev, and it is in this state that the following commands are given:
[INDENT]1st command:[/INDENT]
```
dmesg | grep -i printrbot
```
[INDENT]1st command result:[/INDENT]
```
[ 9299.178030] usb 5-1: Manufacturer: Printrbot
[ 9299.178032] usb 5-1: SerialNumber: Printrbot12345
```
[INDENT]2nd command:[/INDENT]
```
dmesg | grep -i ttyacm0
```
[INDENT]2nd command result:[/INDENT]
```
[ 9299.212459] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
```
[INDENT]3rd command:[/INDENT]
```
ls -ld /dev/ttyACM0
```
[INDENT]3rd command result:[/INDENT]
```
ls: cannot access /dev/ttyACM0: No such file or directory
```
[INDENT]...and "ls -l /dev" shows no ttyACM0 device listed even though the printer is plugged in.[/INDENT]
[*] 4th command:
```
lsusb
```
[INDENT]4th command result:[/INDENT]
```
Bus 002 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 04b8:089e Seiko Epson Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 093a:2521 Pixart Imaging, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
[/LIST]

**_Questions:_**
[LIST=1]
[*] What system configurations can be checked to make sure the printer is being automatically detected when it gets plugged in?
[*] What other troubleshooting steps can be taken to find out why this USB device isn't being automatically detected after subsequent reattachment to the computer?
[/LIST]

Thanks.

---

### Post by landstander on 2015-02-03
A more complete and thorough test of the connection between the computer and the circuit board on the 3D printer revealed that the USB cable was seated to loosely in the USB socket on the circuit board.

After cleaning both the cable and the socket and tightening the connection via crimping one side of the socket so that it pressed connection points between the USB cable and the USB socket of the circuit board together more tightly, the computer was faithfully able to detect the connection state 3D printer each time it was connected or disconnected from the computer.

This thread is solved.

---

