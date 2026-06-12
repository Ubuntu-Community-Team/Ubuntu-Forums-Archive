---
title: "Card Reader not working in Ubuntu, not being detected"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by caesar424 on 2007-06-12
I've read all over Google and the web about the Texas Instruments issue. Tried all those solutions, and the card still isn't working. I really don't know what kind of reader it is... it's mounted in a whitebox system, 9 or 12-in-1, can't remember which is max...

Anyway, here are the **lspci** results from my box:

```
jrhorn@jrhorn-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)
02:01.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 04)
02:03.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
03:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

Not sure where the card reader is, but the TI device listed is actually my firewire card (but you linuxperts already knew that!). Here is an error from my log file:

```
06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   34.588095] usb 3-1: new full speed USB device using uhci_hcd and address 2

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   34.711981] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   34.939782] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   35.019912] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00d0035600b16413]

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   35.155585] usb 3-1: new full speed USB device using uhci_hcd and address 3

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   35.279475] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   35.507267] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   35.723072] usb 3-1: new full speed USB device using uhci_hcd and address 4

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   36.138698] usb 3-1: device not accepting address 4, error -71

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   36.250597] usb 3-1: new full speed USB device using uhci_hcd and address 5

06/12/2007 06:53:45 PM    jrhorn-desktop    kernel    [   36.666224] usb 3-1: device not accepting address 5, error -71


```

And later...

```
06/12/2007 06:53:50 PM    jrhorn-desktop    kernel    [  100.552910] usb 3-1: new full speed USB device using uhci_hcd and address 6

06/12/2007 06:53:50 PM    jrhorn-desktop    kernel    [  100.676798] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:50 PM    jrhorn-desktop    kernel    [  100.904593] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:50 PM    jrhorn-desktop    kernel    [  101.120398] usb 3-1: new full speed USB device using uhci_hcd and address 7

06/12/2007 06:53:51 PM    jrhorn-desktop    kernel    [  101.300236] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:51 PM    jrhorn-desktop    kernel    [  101.528033] usb 3-1: device descriptor read/64, error -71

06/12/2007 06:53:51 PM    jrhorn-desktop    kernel    [  101.743840] usb 3-1: new full speed USB device using uhci_hcd and address 8

06/12/2007 06:53:51 PM    jrhorn-desktop    kernel    [  102.159456] usb 3-1: device not accepting address 8, error -71

06/12/2007 06:53:52 PM    jrhorn-desktop    kernel    [  102.271366] usb 3-1: new full speed USB device using uhci_hcd and address 9

06/12/2007 06:53:52 PM    jrhorn-desktop    kernel    [  102.686984] usb 3-1: device not accepting address 9, error -71


```

Not sure if this helps. Thanks for all the help!

---

### Post by caesar424 on 2007-06-19
Bump... can anyone help with this?

---

### Post by IntuitiveNipple on 2007-06-19
It is likely it is a USB device. Use this command to find any mass storage USB devices:
```
$ sudo lsusb -v | awk '{ if( $0 ~ /^Bus/) { device=$0;} if($0 ~ /Mass Storage/) { print("Mass Storage device " device);}  }'
Password:
Mass Storage device Bus 005 Device 003: ID 054c:0281 Sony Corp.
```

---

### Post by caesar424 on 2007-06-19
> **IntuitiveNipple said:**
> It is likely it is a USB device. Use this command to find any mass storage USB devices:
```
$ sudo lsusb -v | awk '{ if( $0 ~ /^Bus/) { device=$0;} if($0 ~ /Mass Storage/) { print("Mass Storage device " device);}  }'
Password:
Mass Storage device Bus 005 Device 003: ID 054c:0281 Sony Corp.
```

Tried the above command and received no response, just another prompt after entering my sudo password. It is quite possible that the device is a USB device mounted to the case. I'll dig around and see what I can find. Thanks for the info.

Jeff

---

### Post by gordwait on 2007-12-21
It looks like you are having problems with USB cabling. 
I'm having this problem too, with other USB devices, in Ubuntu 7.10. 

The key message is 

 "device not accepting address  7, error -71"

Where the address 7 could be any number.

To see if this is an issue try:

  sudo dmesg | grep "device not accepting"

What seems to be happening is that your PC has hardware support for USB 2 in "High Speed" mode,
but some part of your USB hardware may be having trouble running at that high speed, causing the failure. 

Another batch of users are getting hints of "not enough power" and apparently the newer USB drivers can monitor and limit USB devices that draw too much power from your PC. 

For the High Speed related problems:

One workaround seems to be to stop the linux high speed USB driver (ehci_hcd) by issuing this command:

          sudo modprobe -r ehci_hcd

, which lets the lower speed USB driver run, but which forces all USB devices to run slower. 

Apparently some people have resolved the problem by using a better quality USB cable, 
(which tells you the original cable was not good enough for high speed mode",
and others have resolved it by changing to a different USB port (which tells you the internal cabling on the problem port is not good enough for high speed mode). 

This feature request is in place, and sounds like a good idea to me:

USB 1.1 automatic fallback if 2.0 fails
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/177430/](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/177430/)

More details are here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419)
Extracted:

The workaround is likely to remove the ehci_hcd module by performing this command:

sudo modprobe -r ehci_hcd

If you would like to make this permanent, then do:

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r`

This process can be reversed by removing the /etc/modprobe.d/blacklist-ehci file and rerunning the update-initramfs command.

---

