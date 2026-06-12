---
title: "epson stylus cx 5900 scanner"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by delfick on 2008-03-21
hello

I have an Epson Stylus CX 5900 printer/scanner/copier.

it prints fine

but scanning is just painful.

Basically what happens is, if I run gscan2pdf as root, it will detect my scanner (without root, it doesn't see it) and I can print a page. During a subsequent scan it will stop during it, the light in the scanner returns to it's starting point and the loading bar in gscan2pdf just stops and nothing happens, no matter how long I leave it. (though sometimes it will give errors, saying the device doesn't exist)....

turning it off, unplugging it from the computer, replugging into the computer and turning scanner back on, then trying gscan2pdf again has the same results.

sane-find-scanner gives me this
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x082e [USB2.0 MFP(Hi-Speed)]) at libusb:002:009
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

sudo scanimage -L gives me this
```
device `epson:libusb:002:010' is a Epson CX6000 flatbed scanner
device `epkowa:libusb:002:010' is a Epson Stylus CX5900/CX6000/DX6000 flatbed scanner

```

output of lsusb
```
Bus 002 Device 010: ID 04b8:082e Seiko Epson Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 001: ID 0000:0000 
```

output of cat /proc/bus/usb/devices
```


[...]


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04b8 ProdID=082e Rev= 1.00
S:  Manufacturer=EPSON
S:  Product=USB2.0 MFP(Hi-Speed)
S:  SerialNumber=L31040704102333190
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:* If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=07(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms


[...]


```

does anyone know how to make this work ?
cause I just spent the day searching everywhere, and it just won't work ...

thnx...

btw, I'm running ubuntu hardy (beta, fresh install today), but this was happening in gutsy as well..

---

### Post by delfick on 2008-03-22
dmesg gives me this 
```
[  979.482417] usb 2-1: new high speed USB device using ehci_hcd and address 6
[  979.627160] usb 2-1: configuration #1 chosen from 1 choice
[  979.636863] usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x04B8 pid 0x082E
[  979.656503] scsi9 : SCSI emulation for USB Mass Storage devices
[  979.662309] usb-storage: device found at 6
[  979.662314] usb-storage: waiting for device to settle before scanning
[  984.658860] usb-storage: device scan complete
[  984.662356] scsi 9:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[  984.669759] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[  984.669790] sd 9:0:0:0: Attached scsi generic sg4 type 0
[  991.440176] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanimage' sets config #1
[ 1007.475925] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanimage' sets config #1
[ 1007.871346] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanadf' sets config #1
[ 1007.906138] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanadf' sets config #1
[ 1017.371681] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanadf' sets config #1
[ 1017.415782] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanadf' sets config #1
[ 1036.472001] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanadf' sets config #1
[ 1036.505082] usb 2-1: usbfs: interface 1 claimed by usblp while 'scanadf' sets config #1
```

also, sometimes, like just then, the scanner just stops midway and the light is just sitting there turned off, doing nothing.....

(and /proc/bus/usb doesn't actually appear unless I do "sudo mount -t usbfs usbfs /proc/bus/usb")
edit : adding "usbfs /proc/bus/usb usbfs auto 0 0" to /etc/fstab makes that automatic...

also, I'm now using this [https://bugs.launchpad.net/ubuntu/hardy/+source/sane-backends-extras/1.0.18.12](https://bugs.launchpad.net/ubuntu/hardy/+source/sane-backends-extras/1.0.18.12) due to this bug here [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/180169](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/180169)

---

### Post by teaker1s on 2008-03-22
have you tried to see if epson's iscan is available for your model?

---

### Post by delfick on 2008-03-22
didn't know about that.

I just tried installing it then (and succeeded in installing). But like everything else needs to be run as root to see the device. and it has the same problem as gscan2pdf, and gives the following errors in dmesg.

```
[ 2227.114184] usb 1-1: usbfs: interface 1 claimed by usblp while 'scanimage' sets config #1

```

also, I found this [http://www.kallisti.net.nz/blog/2006/11/ubuntu-and-the-epson-stylus-cx5900/](http://www.kallisti.net.nz/blog/2006/11/ubuntu-and-the-epson-stylus-cx5900/) which solves the permissions problem by putting the following in /etc/udev/rules.d/45-libsane.rules.

```
# Epson CX-5900
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082e", MODE="664", GROUP="scanner"
```

but I have no such file and wouldn't have a clue how to add my own rules....

---

### Post by delfick on 2008-03-23
I solved my permissions problem by putting this

```
none /dev/bus/usb usbfs auto,devmode=0666 0 0
```

in my /etc/fstab file.

other problems still remain....


EDIT : I found the libsane-extras.rules. it's in /etc/udev rather than /etc/udev/rules.d

---

### Post by delfick on 2008-03-23
I filed a bug report [https://bugs.launchpad.net/ubuntu/+bug/205471](https://bugs.launchpad.net/ubuntu/+bug/205471)

---

### Post by delfick on 2008-03-24
another thing I just noticed.

If I set the scan type to binary, I can use any dpi (including 1200) and it works perfectly

if I set the scan type to grey or colour, then it works perfectly if I use 100 dpi, but anything higher causes the problems.

---

### Post by delfick on 2008-03-29
well, I believe I found the source of my problems....

stupid me didn't test my scanner in windows on my main computer to make sure the problem was only in linux. 

Today I needed to put a program from my computer onto my calculator, so I tried connecting my calculator to my computer (in windows first) and found that tilp wouldn't connect to my calculator.

So I booted into linux and tried the linux version of tilp. Again it wouldn't connect to my calculator. 
So I looked at dmesg and it was giving similar errors to those my scanner gives. 

so I looked at the device manager (it's not installed by default in hardy, but it was in gutsy) and it has a weird error message about not being enough power for the device. Which I thought was weird. And then I started to wonder if it was my usb ports that was the problem.

So I booted into windows and sure enough I get the exact same problems in windows as I do in linux. (I've been using my scanner via my laptop and it works perfectly on that, so It's not a scanner issue)

seeing as it screws up in the same way on both windows and linux, that means it's not a software issue, so that leaves the usb ports.

I'm not much of a hardware person so I wouldn't have a clue what to look for, but when I get the chance I'll ask my brother to have a look......

---

