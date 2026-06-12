---
title: "epson stylus dx5000 scanner not working"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by precinto on 2007-01-02
Hello.

I bought a Epson Stylus DX5000. It was correctly recognized (although the model I selected was DX4800, the highest available of the series) and I can't print just fine. But Xsine says there are no obtainable devices. This is my epson.conf

```
# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500, comment out the previous line and uncomment the following line:
#scsi
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0

usb 0x04b8 0x082b 
```
(I just added the last line based on [this page]("http://forums.freestandards.org/read.php?26,84").)

lsusb output:
```
Bus 001 Device 003: ID 04b8:082b Seiko Epson Corp.
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

I also created /etc/hotplug/usb/libsane.usermap in a desperation moment based on [this other page]("http://doc.gwos.org/index.php/Epson_CX6600").

sane-find-scanner output:

```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x082b) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

scanimage -L output:
```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

sudo scanimage -L
```
device `epson:libusb:001:003' is a Epson Unknown model flatbed scanner
```

I also tried 'sudo chmod 666 /proc/bus/usb/001/003' with no luck.

Any help would be appreciated. Thanks in advance.

---

### Post by precinto on 2007-01-02
I don't know exactly what I did. I installed iscan from [http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm) (i had to alien the packages). At first it didn't work, but now, after reinstalling iscan several times because i erased something i shouldn't, it is working.

---

### Post by Rui Pais on 2007-02-01
hi,
i have that exact model and made my work only by add that line to /etc/sane.d/epson.conf

i didn't add nothing to (or even have a) /etc/hotplug/usb/libsane.usermap

didn't change any permissions.

Just work either on 32b as on 64b environment with xsane.
 (iscan is a cool app, but it's closed source and didn't work on 64bit)

hth

---

### Post by Macareno on 2007-03-07
Hi!
You need this steps:

- Add in /etc/sane.d/
usb 0x04b8 0x082b

- And then.. add in  /etc/udev/rules.d/45-libsane.rules
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082b", MODE="664", GROUP="scanner"
(explain: ubuntu uses udev, is necessary add the rights permissions for the hardware)

- enjoy

my first reply :-p

---

### Post by corax on 2007-04-30
Hey thanks Macareno !!!

It worked for me like charm :)

Keep up your good work with posts like this :)

THX !!!

---

