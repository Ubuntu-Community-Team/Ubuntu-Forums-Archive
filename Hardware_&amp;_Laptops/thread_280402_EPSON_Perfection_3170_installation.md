---
title: "EPSON Perfection 3170 installation"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by zion_567 on 2006-10-19
Dear all

I am trying (desparately) to make my EPSON 3170 Perfection scanner work at Ubuntu 6.06 - it is the only thing left for my complete transition to my beloved Ubuntu!

I have installed sane, xsane, libsane and others.

I have tried editing /etc/sane.d/epkowa.conf replacing "usb" with Vendor and Product ID, but no luck.

As /proc/bus/usb/devices says, my scanner is being detected on the USB bus and sane-find-scanner finds it also, but scanimage -L does not list it at all (the same output I get from xsane startup)

Can anybody help me?


Useful outputs:


less /proc/bus/usb/devices

T: Bus=07 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#= 7 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs= 1
P: Vendor=04b8 ProdID=0116 Rev= 1.00
S: Manufacturer=EPSON
S: Product=EPSON Scanner
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr= 2mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E: Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E: Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=31875us



scanimage -L

device `v4l:/dev/video1' is a Noname Pinnacle PCTV 300i DVB-T + PAL virtual device
device `v4l:/dev/video0' is a Noname Creative Nx Pro virtual device




sane-find-scanner

# sane-find-scanner will now attempt to detect your scanner. If the
# result is different from what you expected, first make sure your
# scanner is powered up and properly connected to your computer.

# No SCSI scanners found. If you expected something different, make sure that
# you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0116) at libusb:007:007
found USB scanner (vendor=0x041e, product=0x401e) at libusb:001:004
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.

# Not checking for parallel port scanners.

# Most Scanners connected to the parallel port or other proprietary ports
# can't be detected by this program.

# You may want to run

---

