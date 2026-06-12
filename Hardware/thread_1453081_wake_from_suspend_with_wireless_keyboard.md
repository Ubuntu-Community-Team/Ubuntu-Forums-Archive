---
title: "wake from suspend with wireless keyboard"
date: 2010-04-12
forum: Hardware
---

### Post by rorzer on 2010-04-12
Hi all,

I'm running Lucid beta on my laptop which I'm planning on running through my LCD tv as a media center/web kiosk. I just got myself a shiny new Riitek micro wireless keyboard/mouse (Vendor=1997 Product=0409 Version=0111).

[engadget review]("http://http://www.engadget.com/2010/03/05/rii-mini-wireless-keyboard-is-perfect-for-your-htpc-not-your-wi/")

It works great, except I can't use it to wake my box from sleep.

I can use my ordinary USB keyboard to wake from sleep, but not the wireless one.

```
root@craptop:~# cat /proc/acpi/wakeup 
Device	S-state	  Status   Sysfs node
LID	  S3	*enabled   
PBTN	  S4	*enabled   
MBTN	  S5	 disabled  
PCI0	  S3	 disabled  no-bus:pci0000:00
USB0	  S3	 enabled   pci:0000:00:1d.0
USB1	  S3	 enabled   pci:0000:00:1d.1
USB2	  S3	 enabled   pci:0000:00:1d.2
USB3	  S3	 enabled   pci:0000:00:1d.3
EHCI	  S3	 enabled   pci:0000:00:1d.7
AZAL	  S3	 disabled  pci:0000:00:1b.0
PCIE	  S4	 disabled  pci:0000:00:1e.0
RP01	  S3	 disabled  pci:0000:00:1c.0
RP02	  S4	 disabled  pci:0000:00:1c.1
RP03	  S3	 disabled  
RP04	  S3	 disabled  pci:0000:00:1c.3
RP05	  S3	 disabled  
RP06	  S3	 disabled  
```


Any ideas?  

[This post]("http://http://permalink.gmane.org/gmane.linux.usb.general/28677") from Alan Stern seems to suggest that only some devices should get USB wakeup privileges from the kernel.  I'm wondering if my device isn't being recognised as a keyboard by usbcore.

However, this seems to suggest that it is working as a keyboard just fine:

```
root@craptop:~#  cat /proc/bus/input/devices
I: Bus=0003 Vendor=1997 Product=0409 Version=0111
N: Name="Riitek Micro Keyboard"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input22
U: Uniq=
H: Handlers=kbd event14 
B: EV=120013
B: KEY=e080ffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=1997 Product=0409 Version=0111
N: Name="Riitek Micro Keyboard"
P: Phys=usb-0000:00:1d.2-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input23
U: Uniq=
H: Handlers=kbd mouse3 event15 
B: EV=1f
B: KEY=837fff002c3027 bf00444400000000 70001 c040a27c000 267bfad9415fed 8e000000000000 0
B: REL=143
B: ABS=100000000
B: MSC=10
```

---

