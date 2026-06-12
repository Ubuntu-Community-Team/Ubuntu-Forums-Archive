---
title: "Install Brother 7055 - Ubuntu"
date: 2013-03-31
forum: Hardware
---

### Post by jorgemmlmg on 2013-03-31
hello,
My knowledge is very low about Linux. and I need help to install my Printer/scanner Brother 7055 in Ubuntu.
The printer is OK, i can print, 
 but i can not scan a document, or choose may new scanner (i have an HP 4480 Printer/Scanner(old) and a Brother 7055 Printer/Scanner)(new)).
Tank You.

---

### Post by glln0v on 2013-03-31
You may need to install the Xsane package and also setup some config, find instructions at the brother website:  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)  Here's what I had to do to get it to work with the Xsane package: 1) Alt+F2 2) gksu gedit /lib/udev/rules.d/40-libsane.rules 3) add the following before the line "# The following rule will disable" # Brother scanner ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes" 4) restart computer for this change to take effect

---

### Post by gifford on 2013-03-31
I assume the DCP-7055 is USB attached and not network, I this correct? As for the scanner, you will need to download the brscan4 driver from the Brother site and follow the install instructions.
Also, you will need to know what version Ubuntu you are using, 12.04, 12.10, etc., and whether it is 32 or 64 bit.
After you have configured the drivers, Xsane should pick it up.

The more information you give about your system and set up the easier it is to help to find the solution.

---

### Post by oswald8361 on 2013-04-27
I have the same problem.
After installation of the Brother DCP-7055 drivers, the printer works fine, but the scanner does not work.
I am using 12.04 32 bits.
The DCP-7055 is USB connected and not network.
But Simple Scane or Xsane give an error message.

Thank you for your help.
I give below some more informations in order to help to find the solution.



```

~$ dpkg -l | grep brscan
ii  brscan-skey      0.2.4-0             Brother Linux scanner S-KEY tool
ii  brscan4          0.4.1-3             Brother Scanner Driver
~$ 

```


```

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 093a:2463 Pixart Imaging, Inc. 
Bus 003 Device 003: ID 04f9:0248 Brother Industries, Ltd 
~$ 

```




```

~$ brscan-skey -l
~$ 

```

```

~$ sudo brscan-skey -l
~$ 

```

```

~$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x0248) at libusb:003:003
found USB scanner (vendor=0x093a, product=0x2463) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
~$ 

```

```

~$ brscan-skey --diagnosis
~$ -------/opt/brother/scanner/brscan4/brsaneconfig4  -d-------
-----------------------------
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=be308b79-de66-4b40-9613-e01f4a8f717c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=16cb3348-4092-4c89-b789-dfbccc913ce7 none            swap    sw              0       0
# (identifier)      (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=45EE3F2D332B54FA   /home    ntfs          nosuid,nodev       0       2 


-----------------------------
sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x0248) at libusb:003:003
found USB scanner (vendor=0x093a, product=0x2463) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
-----------------------------
ls -R -all /proc/bus/usb
ls: impossible d'accéder à /proc/bus/usb: Aucun fichier ou dossier de ce type
-----------------------------
cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: Aucun fichier ou dossier de ce type
-----------------------------
scanimage -L
device `brother4:bus2;dev1' is a Brother *DCP-7055 USB scanner
-----------------------------
-----------------------------
/etc/opt/brother/scanner/brscan4//brsanenetdevice4.cfg:
-----------------------------
/etc/opt/brother/scanner/brscan4//Brsane4.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_4.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_1.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_2.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_5.ini:
-----------------------------
/etc/opt/brother/scanner/brscan4//models4/ext_3.ini:
-----------------------------
-----------------------------
ping
/opt/brother/scanner/brscan4/brsaneconfig4  -d
------- cat /opt/brother/scanner/brscan-skey/brscan-skey-0.2.4-0.cfg-------
password=
IMAGE="sh  /opt/brother/scanner/brscan-skey/script/scantoimage-0.2.4-0.sh"
OCR="sh  /opt/brother/scanner/brscan-skey/script/scantoocr-0.2.4-0.sh"
EMAIL="sh  /opt/brother/scanner/brscan-skey/script/scantoemail-0.2.4-0.sh"
FILE="sh  /opt/brother/scanner/brscan-skey/script/scantofile-0.2.4-0.sh"
SEMID=b

```

```

~$ scanimage -L
device `brother4:bus2;dev1' is a Brother *DCP-7055 USB scanner
~$ 

```

```

~$ scanimage > image.pnm
scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567
scanimage: sane_start: Invalid argument
~$ 

```

```

~$ sudo scanimage > image.pnm
[sudo] password for x: 
scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567
scanimage: sane_start: Invalid argument
~$ 

```

```

~$ sudo cat /sys/kernel/debug/usb/devices

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev= 3.02
S:  Manufacturer=Linux 3.2.0-40-generic-pae xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 4
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.02
S:  Manufacturer=Linux 3.2.0-40-generic-pae xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12   MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=093a ProdID=2463 Rev= 1.00
S:  Manufacturer=Pixart Imaging Inc. 
S:  Product=CIF Single Chip     
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 1 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 128 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 2 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 256 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 3 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 384 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 4 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 512 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 5 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 640 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 6 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 768 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 7 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 896 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 8 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=pac207
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS=1023 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  4 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04f9 ProdID=0248 Rev= 1.00
S:  SerialNumber=E69742L2N788703
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=4096ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 2
B:  Alloc=  0/800 us ( 0%), #Int=  1, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.02
S:  Manufacturer=Linux 3.2.0-40-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480  MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480  MxCh= 2
B:  Alloc=  0/800 us ( 0%), #Int=  1, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 3.02
S:  Manufacturer=Linux 3.2.0-40-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480  MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  6 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b307 Rev=60.30
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=TOSHIBA Web Camera - HD
S:  SerialNumber=0x0001
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
A:  FirstIf#= 0 IfCount= 2 Cls=0e(video) Sub=03 Prot=00
I:* If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=4ms
I:* If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 1 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 128 Ivl=125us
I:  If#= 1 Alt= 2 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 512 Ivl=125us
I:  If#= 1 Alt= 3 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1024 Ivl=125us
I:  If#= 1 Alt= 4 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1536 Ivl=125us
I:  If#= 1 Alt= 5 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2048 Ivl=125us
I:  If#= 1 Alt= 6 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2688 Ivl=125us
I:  If#= 1 Alt= 7 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=3072 Ivl=125us
~$ 

```

```

~$ SANE_DEBUG_DLL=4 scanimage > toto.pnm 2>error.log
~$ 

```

and here is the content of the error.log file :
```

[sanei_debug] Setting debug level of dll to 4.
[dll] sane_init: SANE dll backend version 1.0.13 from sane-backends 1.0.22
[dll] sane_init/read_dlld: attempting to open directory `./dll.d'
[dll] sane_init/read_dlld: attempting to open directory `/etc/sane.d/dll.d'
[dll] sane_init/read_dlld: using config directory `/etc/sane.d/dll.d'
[dll] add_backend: adding backend `ls5000'
[dll] add_backend: adding backend `hpaio'
[dll] add_backend: adding backend `net'
[dll] add_backend: adding backend `abaton'
[dll] add_backend: adding backend `agfafocus'
[dll] add_backend: adding backend `apple'
[dll] add_backend: adding backend `avision'
[dll] add_backend: adding backend `artec'
[dll] add_backend: adding backend `artec_eplus48u'
[dll] add_backend: adding backend `as6e'
[dll] add_backend: adding backend `bh'
[dll] add_backend: adding backend `canon'
[dll] add_backend: adding backend `canon630u'
[dll] add_backend: adding backend `canon_dr'
[dll] add_backend: adding backend `cardscan'
[dll] add_backend: adding backend `coolscan'
[dll] add_backend: adding backend `coolscan3'
[dll] add_backend: adding backend `dell1600n_net'
[dll] add_backend: adding backend `dmc'
[dll] add_backend: adding backend `epjitsu'
[dll] add_backend: adding backend `epson2'
[dll] add_backend: adding backend `fujitsu'
[dll] add_backend: adding backend `genesys'
[dll] add_backend: adding backend `gt68xx'
[dll] add_backend: adding backend `hp'
[dll] add_backend: adding backend `hp3900'
[dll] add_backend: adding backend `hpsj5s'
[dll] add_backend: adding backend `hp3500'
[dll] add_backend: adding backend `hp4200'
[dll] add_backend: adding backend `hp5400'
[dll] add_backend: adding backend `hp5590'
[dll] add_backend: adding backend `hpljm1005'
[dll] add_backend: adding backend `hs2p'
[dll] add_backend: adding backend `ibm'
[dll] add_backend: adding backend `kodak'
[dll] add_backend: adding backend `kvs1025'
[dll] add_backend: adding backend `kvs20xx'
[dll] add_backend: adding backend `leo'
[dll] add_backend: adding backend `lexmark'
[dll] add_backend: adding backend `ma1509'
[dll] add_backend: adding backend `magicolor'
[dll] add_backend: adding backend `matsushita'
[dll] add_backend: adding backend `microtek'
[dll] add_backend: adding backend `microtek2'
[dll] add_backend: adding backend `mustek'
[dll] add_backend: adding backend `mustek_usb'
[dll] add_backend: adding backend `mustek_usb2'
[dll] add_backend: adding backend `nec'
[dll] add_backend: adding backend `niash'
[dll] add_backend: adding backend `pie'
[dll] add_backend: adding backend `pixma'
[dll] add_backend: adding backend `plustek'
[dll] add_backend: adding backend `qcam'
[dll] add_backend: adding backend `ricoh'
[dll] add_backend: adding backend `rts8891'
[dll] add_backend: adding backend `s9036'
[dll] add_backend: adding backend `sceptre'
[dll] add_backend: adding backend `sharp'
[dll] add_backend: adding backend `sm3600'
[dll] add_backend: adding backend `sm3840'
[dll] add_backend: adding backend `snapscan'
[dll] add_backend: adding backend `sp15c'
[dll] add_backend: adding backend `tamarack'
[dll] add_backend: adding backend `teco1'
[dll] add_backend: adding backend `teco2'
[dll] add_backend: adding backend `teco3'
[dll] add_backend: adding backend `u12'
[dll] add_backend: adding backend `umax'
[dll] add_backend: adding backend `umax1220u'
[dll] add_backend: adding backend `v4l'
[dll] add_backend: adding backend `xerox_mfp'
[dll] add_backend: adding backend `brother4'
[dll] sane_get_devices
[dll] load: searching backend `brother4' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-brother4.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-brother4.so.1'
[dll] init: initializing backend `brother4'
[dll] init: backend `brother4' is version 1.0.1
[dll] load: searching backend `xerox_mfp' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-xerox_mfp.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-xerox_mfp.so.1'
[dll] init: initializing backend `xerox_mfp'
[dll] init: backend `xerox_mfp' is version 1.0.12
[dll] load: searching backend `v4l' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-v4l.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-v4l.so.1'
[dll] init: initializing backend `v4l'
[dll] init: backend `v4l' is version 1.0.5
[dll] load: searching backend `umax1220u' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-umax1220u.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-umax1220u.so.1'
[dll] init: initializing backend `umax1220u'
[dll] init: backend `umax1220u' is version 1.0.2
[dll] load: searching backend `umax' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-umax.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-umax.so.1'
[dll] init: initializing backend `umax'
[dll] init: backend `umax' is version 1.0.45
[dll] load: searching backend `u12' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-u12.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-u12.so.1'
[dll] init: initializing backend `u12'
[dll] init: backend `u12' is version 1.0.0
[dll] load: searching backend `teco3' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-teco3.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-teco3.so.1'
[dll] init: initializing backend `teco3'
[dll] init: backend `teco3' is version 1.0.1
[dll] load: searching backend `teco2' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-teco2.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-teco2.so.1'
[dll] init: initializing backend `teco2'
[dll] init: backend `teco2' is version 1.0.10
[dll] load: searching backend `teco1' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-teco1.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-teco1.so.1'
[dll] init: initializing backend `teco1'
[dll] init: backend `teco1' is version 1.0.10
[dll] load: searching backend `tamarack' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-tamarack.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-tamarack.so.1'
[dll] init: initializing backend `tamarack'
[dll] init: backend `tamarack' is version 1.0.0
[dll] load: searching backend `sp15c' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-sp15c.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-sp15c.so.1'
[dll] init: initializing backend `sp15c'
[dll] init: backend `sp15c' is version 1.0.0
[dll] load: searching backend `snapscan' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-snapscan.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-snapscan.so.1'
[dll] init: initializing backend `snapscan'
[dll] init: backend `snapscan' is version 1.4.53
[dll] load: searching backend `sm3840' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-sm3840.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-sm3840.so.1'
[dll] init: initializing backend `sm3840'
[dll] init: backend `sm3840' is version 1.0.0
[dll] load: searching backend `sm3600' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-sm3600.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-sm3600.so.1'
[dll] init: initializing backend `sm3600'
[dll] init: backend `sm3600' is version 1.0.6
[dll] load: searching backend `sharp' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-sharp.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-sharp.so.1'
[dll] init: initializing backend `sharp'
[dll] init: backend `sharp' is version 1.0.0
[dll] load: searching backend `sceptre' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-sceptre.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-sceptre.so.1'
[dll] init: initializing backend `sceptre'
[dll] init: backend `sceptre' is version 1.0.10
[dll] load: searching backend `s9036' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-s9036.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-s9036.so.1'
[dll] init: initializing backend `s9036'
[dll] init: backend `s9036' is version 1.0.0
[dll] load: searching backend `rts8891' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-rts8891.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-rts8891.so.1'
[dll] init: initializing backend `rts8891'
[dll] init: backend `rts8891' is version 1.0.31
[dll] load: searching backend `ricoh' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-ricoh.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-ricoh.so.1'
[dll] init: initializing backend `ricoh'
[dll] init: backend `ricoh' is version 1.0.0
[dll] load: searching backend `qcam' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-qcam.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-qcam.so.1'
[dll] init: initializing backend `qcam'
[dll] init: backend `qcam' is version 1.0.0
[dll] load: searching backend `plustek' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-plustek.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-plustek.so.1'
[dll] init: initializing backend `plustek'
[dll] init: backend `plustek' is version 1.0.0
[dll] load: searching backend `pixma' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-pixma.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-pixma.so.1'
[dll] init: initializing backend `pixma'
[dll] init: backend `pixma' is version 1.0.16
[dll] load: searching backend `pie' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-pie.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-pie.so.1'
[dll] init: initializing backend `pie'
[dll] init: backend `pie' is version 1.0.9
[dll] load: searching backend `niash' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-niash.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-niash.so.1'
[dll] init: initializing backend `niash'
[dll] init: backend `niash' is version 1.0.1
[dll] load: searching backend `nec' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-nec.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-nec.so.1'
[dll] init: initializing backend `nec'
[dll] init: backend `nec' is version 1.0.0
[dll] load: searching backend `mustek_usb2' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-mustek_usb2.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-mustek_usb2.so.1'
[dll] init: initializing backend `mustek_usb2'
[dll] init: backend `mustek_usb2' is version 1.0.10
[dll] load: searching backend `mustek_usb' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-mustek_usb.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-mustek_usb.so.1'
[dll] init: initializing backend `mustek_usb'
[dll] init: backend `mustek_usb' is version 1.0.18
[dll] load: searching backend `mustek' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-mustek.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-mustek.so.1'
[dll] init: initializing backend `mustek'
[dll] init: backend `mustek' is version 1.0.138
[dll] load: searching backend `microtek2' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-microtek2.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-microtek2.so.1'
[dll] init: initializing backend `microtek2'
[dll] init: backend `microtek2' is version 1.0.0
[dll] load: searching backend `microtek' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-microtek.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-microtek.so.1'
[dll] init: initializing backend `microtek'
[dll] init: backend `microtek' is version 1.0.0
[dll] load: searching backend `matsushita' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-matsushita.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-matsushita.so.1'
[dll] init: initializing backend `matsushita'
[dll] init: backend `matsushita' is version 1.0.7
[dll] load: searching backend `magicolor' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-magicolor.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-magicolor.so.1'
[dll] init: initializing backend `magicolor'
[dll] init: backend `magicolor' is version 1.0.1
[dll] load: searching backend `ma1509' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-ma1509.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-ma1509.so.1'
[dll] init: initializing backend `ma1509'
[dll] init: backend `ma1509' is version 1.0.3
[dll] load: searching backend `lexmark' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-lexmark.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-lexmark.so.1'
[dll] init: initializing backend `lexmark'
[dll] init: backend `lexmark' is version 1.0.30
[dll] load: searching backend `leo' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-leo.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-leo.so.1'
[dll] init: initializing backend `leo'
[dll] init: backend `leo' is version 1.0.11
[dll] load: searching backend `kvs20xx' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-kvs20xx.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-kvs20xx.so.1'
[dll] init: initializing backend `kvs20xx'
[dll] init: backend `kvs20xx' is version 1.0.2
[dll] load: searching backend `kvs1025' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-kvs1025.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-kvs1025.so.1'
[dll] init: initializing backend `kvs1025'
[dll] init: backend `kvs1025' is version 1.0.3
[dll] load: searching backend `kodak' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-kodak.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-kodak.so.1'
[dll] init: initializing backend `kodak'
[dll] init: backend `kodak' is version 1.0.7
[dll] load: searching backend `ibm' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-ibm.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-ibm.so.1'
[dll] init: initializing backend `ibm'
[dll] init: backend `ibm' is version 1.0.0
[dll] load: searching backend `hs2p' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hs2p.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hs2p.so.1'
[dll] init: initializing backend `hs2p'
[dll] init: backend `hs2p' is version 1.0.0
[dll] load: searching backend `hpljm1005' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hpljm1005.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hpljm1005.so.1'
[dll] init: initializing backend `hpljm1005'
[dll] init: backend `hpljm1005' is version 1.0.1
[dll] load: searching backend `hp5590' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hp5590.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hp5590.so.1'
[dll] init: initializing backend `hp5590'
[dll] init: backend `hp5590' is version 1.0.5
[dll] load: searching backend `hp5400' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hp5400.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hp5400.so.1'
[dll] init: initializing backend `hp5400'
[dll] init: backend `hp5400' is version 1.0.3
[dll] load: searching backend `hp4200' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hp4200.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hp4200.so.1'
[dll] init: initializing backend `hp4200'
[dll] init: backend `hp4200' is version 1.0.0
[dll] load: searching backend `hp3500' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hp3500.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hp3500.so.1'
[dll] init: initializing backend `hp3500'
[dll] init: backend `hp3500' is version 1.0.0
[dll] load: searching backend `hpsj5s' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hpsj5s.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hpsj5s.so.1'
[dll] init: initializing backend `hpsj5s'
[dll] init: backend `hpsj5s' is version 1.0.3
[dll] load: searching backend `hp3900' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hp3900.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hp3900.so.1'
[dll] init: initializing backend `hp3900'
[dll] init: backend `hp3900' is version 1.0.0
[dll] load: searching backend `hp' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hp.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-hp.so.1'
[dll] init: initializing backend `hp'
[dll] init: backend `hp' is version 1.0.8
[dll] load: searching backend `gt68xx' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-gt68xx.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-gt68xx.so.1'
[dll] init: initializing backend `gt68xx'
[dll] init: backend `gt68xx' is version 1.0.84
[dll] load: searching backend `genesys' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-genesys.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-genesys.so.1'
[dll] init: initializing backend `genesys'
[dll] init: backend `genesys' is version 1.0.63
[dll] load: searching backend `fujitsu' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-fujitsu.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-fujitsu.so.1'
[dll] init: initializing backend `fujitsu'
[dll] init: backend `fujitsu' is version 1.0.106
[dll] load: searching backend `epson2' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-epson2.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-epson2.so.1'
[dll] init: initializing backend `epson2'
[dll] init: backend `epson2' is version 1.0.124
[dll] load: searching backend `epjitsu' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-epjitsu.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-epjitsu.so.1'
[dll] init: initializing backend `epjitsu'
[dll] init: backend `epjitsu' is version 1.0.20
[dll] load: searching backend `dmc' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-dmc.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-dmc.so.1'
[dll] init: initializing backend `dmc'
[dll] init: backend `dmc' is version 1.0.0
[dll] load: searching backend `dell1600n_net' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-dell1600n_net.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-dell1600n_net.so.1'
[dll] init: initializing backend `dell1600n_net'
[dll] init: backend `dell1600n_net' is version 1.0.0
[dll] load: searching backend `coolscan3' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-coolscan3.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-coolscan3.so.1'
[dll] init: initializing backend `coolscan3'
[dll] init: backend `coolscan3' is version 1.0.0
[dll] load: searching backend `coolscan' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-coolscan.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-coolscan.so.1'
[dll] init: initializing backend `coolscan'
[dll] init: backend `coolscan' is version 1.0.0
[dll] load: searching backend `cardscan' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-cardscan.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-cardscan.so.1'
[dll] init: initializing backend `cardscan'
[dll] init: backend `cardscan' is version 1.0.2
[dll] load: searching backend `canon_dr' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-canon_dr.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-canon_dr.so.1'
[dll] init: initializing backend `canon_dr'
[dll] init: backend `canon_dr' is version 1.0.37
[dll] load: searching backend `canon630u' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-canon630u.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-canon630u.so.1'
[dll] init: initializing backend `canon630u'
[dll] init: backend `canon630u' is version 1.0.1
[dll] load: searching backend `canon' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-canon.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-canon.so.1'
[dll] init: initializing backend `canon'
[dll] init: backend `canon' is version 1.0.0
[dll] load: searching backend `bh' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-bh.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-bh.so.1'
[dll] init: initializing backend `bh'
[dll] init: backend `bh' is version 1.0.4
[dll] load: searching backend `as6e' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-as6e.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-as6e.so.1'
[dll] init: initializing backend `as6e'
[dll] load: searching backend `artec_eplus48u' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-artec_eplus48u.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-artec_eplus48u.so.1'
[dll] init: initializing backend `artec_eplus48u'
[dll] init: backend `artec_eplus48u' is version 1.0.0
[dll] load: searching backend `artec' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-artec.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-artec.so.1'
[dll] init: initializing backend `artec'
[dll] init: backend `artec' is version 1.0.0
[dll] load: searching backend `avision' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-avision.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-avision.so.1'
[dll] init: initializing backend `avision'
[dll] init: backend `avision' is version 1.0.294
[dll] load: searching backend `apple' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-apple.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-apple.so.1'
[dll] init: initializing backend `apple'
[dll] init: backend `apple' is version 1.0.0
[dll] load: searching backend `agfafocus' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-agfafocus.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-agfafocus.so.1'
[dll] init: initializing backend `agfafocus'
[dll] init: backend `agfafocus' is version 1.0.0
[dll] load: searching backend `abaton' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-abaton.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-abaton.so.1'
[dll] init: initializing backend `abaton'
[dll] init: backend `abaton' is version 1.0.0
[dll] load: searching backend `net' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-net.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-net.so.1'
[dll] init: initializing backend `net'
[dll] init: backend `net' is version 1.0.22
[dll] load: searching backend `hpaio' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-hpaio.so.1'
[dll] load: couldn't open `/usr/lib/i386-linux-gnu/sane/libsane-hpaio.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-hpaio.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpaio.so.1'
[dll] init: initializing backend `hpaio'
[dll] init: backend `hpaio' is version 1.0.0
[dll] load: searching backend `ls5000' in `/usr/lib/i386-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/i386-linux-gnu/sane/libsane-ls5000.so.1'
[dll] load: dlopen()ing `/usr/lib/i386-linux-gnu/sane/libsane-ls5000.so.1'
[dll] init: initializing backend `ls5000'
[dll] init: backend `ls5000' is version 1.0.0
[dll] sane_get_devices: found 1 devices
[dll] sane_open: trying to open `brother4:bus2;dev1'
[dll] sane_open: open successful
[dll] sane_get_option_descriptor(handle=0x9958f48,option=0)
[dll] sane_control_option(handle=0x9958f48,option=0,action=0,value=0xbf9cd548,info=(nil))
[dll] sane_get_option_descriptor(handle=0x9958f48,option=0)
[dll] sane_control_option(handle=0x9958f48,option=0,action=0,value=0xbf9cd478,info=(nil))
[dll] sane_get_option_descriptor(handle=0x9958f48,option=1)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=2)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=3)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=4)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=5)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=6)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=7)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=8)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=9)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=10)
[dll] sane_get_option_descriptor(handle=0x9958f48,option=11)
[dll] sane_control_option(handle=0x9958f48,option=10,action=0,value=0x80533f0,info=(nil))
[dll] sane_control_option(handle=0x9958f48,option=8,action=0,value=0xbf9cd47c,info=(nil))
[dll] sane_control_option(handle=0x9958f48,option=11,action=0,value=0x80533f4,info=(nil))
[dll] sane_control_option(handle=0x9958f48,option=9,action=0,value=0xbf9cd47c,info=(nil))
[dll] sane_control_option(handle=0x9958f48,option=8,action=0,value=0xbf9cd550,info=(nil))
[dll] sane_get_option_descriptor(handle=0x9958f48,option=10)
[dll] sane_control_option(handle=0x9958f48,option=10,action=1,value=0xbf9cd554,info=0xbf9cd47c)
scanimage: rounded value of br-x from 215.9 to 215.88
[dll] sane_control_option(handle=0x9958f48,option=9,action=0,value=0xbf9cd550,info=(nil))
[dll] sane_get_option_descriptor(handle=0x9958f48,option=11)
[dll] sane_control_option(handle=0x9958f48,option=11,action=1,value=0xbf9cd554,info=0xbf9cd47c)
scanimage: rounded value of br-y from 355.6 to 355.567
[dll] sane_start(handle=0x9958f48)
scanimage: sane_start: Invalid argument
[dll] sane_cancel(handle=0x9958f48)
[dll] sane_close(handle=0x9958f48)
[dll] sane_exit: exiting
[dll] sane_exit: calling backend `brother4's exit function
[dll] sane_exit: calling backend `xerox_mfp's exit function
[dll] sane_exit: calling backend `v4l's exit function
[dll] sane_exit: calling backend `umax1220u's exit function
[dll] sane_exit: calling backend `umax's exit function
[dll] sane_exit: calling backend `u12's exit function
[dll] sane_exit: calling backend `teco3's exit function
[dll] sane_exit: calling backend `teco2's exit function
[dll] sane_exit: calling backend `teco1's exit function
[dll] sane_exit: calling backend `tamarack's exit function
[dll] sane_exit: calling backend `sp15c's exit function
[dll] sane_exit: calling backend `snapscan's exit function
[dll] sane_exit: calling backend `sm3840's exit function
[dll] sane_exit: calling backend `sm3600's exit function
[dll] sane_exit: calling backend `sharp's exit function
[dll] sane_exit: calling backend `sceptre's exit function
[dll] sane_exit: calling backend `s9036's exit function
[dll] sane_exit: calling backend `rts8891's exit function
[dll] sane_exit: calling backend `ricoh's exit function
[dll] sane_exit: calling backend `qcam's exit function
[dll] sane_exit: calling backend `plustek's exit function
[dll] sane_exit: calling backend `pixma's exit function
[dll] sane_exit: calling backend `pie's exit function
[dll] sane_exit: calling backend `niash's exit function
[dll] sane_exit: calling backend `nec's exit function
[dll] sane_exit: calling backend `mustek_usb2's exit function
[dll] sane_exit: calling backend `mustek_usb's exit function
[dll] sane_exit: calling backend `mustek's exit function
[dll] sane_exit: calling backend `microtek2's exit function
[dll] sane_exit: calling backend `microtek's exit function
[dll] sane_exit: calling backend `matsushita's exit function
[dll] sane_exit: calling backend `magicolor's exit function
[dll] sane_exit: calling backend `ma1509's exit function
[dll] sane_exit: calling backend `lexmark's exit function
[dll] sane_exit: calling backend `leo's exit function
[dll] sane_exit: calling backend `kvs20xx's exit function
[dll] sane_exit: calling backend `kvs1025's exit function
[dll] sane_exit: calling backend `kodak's exit function
[dll] sane_exit: calling backend `ibm's exit function
[dll] sane_exit: calling backend `hs2p's exit function
[dll] sane_exit: calling backend `hpljm1005's exit function
[dll] sane_exit: calling backend `hp5590's exit function
[dll] sane_exit: calling backend `hp5400's exit function
[dll] sane_exit: calling backend `hp4200's exit function
[dll] sane_exit: calling backend `hp3500's exit function
[dll] sane_exit: calling backend `hpsj5s's exit function
[dll] sane_exit: calling backend `hp3900's exit function
[dll] sane_exit: calling backend `hp's exit function
[dll] sane_exit: calling backend `gt68xx's exit function
[dll] sane_exit: calling backend `genesys's exit function
[dll] sane_exit: calling backend `fujitsu's exit function
[dll] sane_exit: calling backend `epson2's exit function
[dll] sane_exit: calling backend `epjitsu's exit function
[dll] sane_exit: calling backend `dmc's exit function
[dll] sane_exit: calling backend `dell1600n_net's exit function
[dll] sane_exit: calling backend `coolscan3's exit function
[dll] sane_exit: calling backend `coolscan's exit function
[dll] sane_exit: calling backend `cardscan's exit function
[dll] sane_exit: calling backend `canon_dr's exit function
[dll] sane_exit: calling backend `canon630u's exit function
[dll] sane_exit: calling backend `canon's exit function
[dll] sane_exit: calling backend `bh's exit function
[dll] sane_exit: calling backend `artec_eplus48u's exit function
[dll] sane_exit: calling backend `artec's exit function
[dll] sane_exit: calling backend `avision's exit function
[dll] sane_exit: calling backend `apple's exit function
[dll] sane_exit: calling backend `agfafocus's exit function
[dll] sane_exit: calling backend `abaton's exit function
[dll] sane_exit: calling backend `net's exit function
[dll] sane_exit: calling backend `hpaio's exit function
[dll] sane_exit: calling backend `ls5000's exit function
[dll] sane_exit: finished

```



and in the file /lib/udev/rules.d/40-libsane.rules :
```

LABEL="libsane_usb_rules_begin"

# Brother Scanner DCP-7055
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0248", ENV{libsane_matched}="yes"

```

or else :
```

~$ cat /lib/udev/rules.d/40-libsane.rules | grep 04f9
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0248", ENV{libsane_matched}="yes"
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="2038", ENV{libsane_matched}="yes"
~$ 

```

---

### Post by danfan46 on 2013-09-13
Oswald, I'm having the same problem. Did you find a solution?

---

### Post by oswald8361 on 2013-09-17
No. Up to now, I didn't find a solution.

---

### Post by daniel97 on 2013-11-14
Hey!
i had the same problems but i think i get a solution (sorry for my bad english). By the way i'm using elementary os.

I also installed the drivers for printer an scanner, printer works, scanner not. By using simplescan and xsane i got an error message (Coud not start scanner/invalid arguments or something like that).

But when staring xsane and first click on "preview" or "preview scan" (don't now the button on the englisch version) it will scan a preview of the document, after that you can click "scan" and it works..

Hope i can help some people.

Mugli

---

### Post by oswald8361 on 2013-11-14
Thanks Daniel,

for this quite simple workaround.
It did work for me, and it helps a lot !

---

### Post by supermandodi on 2014-03-14
Here is a bash file that Brother supply that solved all my problems
[http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625]("http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625")

---

### Post by supermandodi on 2014-03-14
Here is a bash file that Brother supply that solved all my problems
[http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625]("http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625")

---

### Post by pdc on 2014-03-14
thanks supermandoli; ..........I am reading it as installing the printer driver and I wondered if it also installed the scanner driver for you?

ie the DCP-7055 seems to be a brscan4 model

---

### Post by oswald8361 on 2014-07-15
The bash file provided by Brother makes the installation easier,
but it does not correct the bug for the scanner.
I ended up with exactly the same problem and same behaviour.

---

