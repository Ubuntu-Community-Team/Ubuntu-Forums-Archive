---
title: "Brother DCP-197C - Scanner not working in Ubuntu 18.10"
date: 2018-12-30
forum: Hardware
---

### Post by cacodemon79 on 2018-12-30
Hi friends,
I can't use my scanner Brother DCP-197C in Ubuntu 18.10.
I installed the Brother drivers: the printer works, the scanner does not work.
Here below some tests.

**lsusb**
```
Bus 002 Device 004: ID 1164:1f08 YUAN High-Tech Development Co., Ltd 
Bus 002 Device 003: ID 064e:a115 Suyin Corp. 
Bus 002 Device 002: ID 1c7a:0801 LighTuning Technology Inc. Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04f9:023e Brother Industries, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**dpkg -l | grep Brother**
```

ii  brother-udev-rule-type1                    1.0.2                                         all          Brother udev rule type 1
ii  brscan-skey                                0.2.4-1                                       amd64        Brother Linux scanner S-KEY tool
ii  brscan3                                    0.2.13-1                                      amd64        Brother Scanner Driver
ii  dcp197ccupswrapper:i386                    1.1.3-1                                       i386         Brother CUPS Inkjet Printer Definitions
ii  dcp197clpr:i386                            1.1.3-1                                       i386         Brother lpr Inkjet Printer Definitions
ii  printer-driver-brlaser                     4-1                                           amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                      1.4.2-3                                       amd64        printer driver Brother P-touch label printers

```

**dpkg -l | grep sane**
```

ii  libsane-common                             1.0.27-1                                      all          API library for scanners -- documentation and support files
ii  libsane-extras:amd64                       1.0.22.6                                      amd64        API library for scanners -- extra backends
ii  libsane-extras-common                      1.0.22.6                                      all          API library for scanners -- documentation and support files
ii  libsane-hpaio:amd64                        3.18.7+dfsg1-2ubuntu2                         amd64        HP SANE backend for multi-function peripherals
ii  libsane1:amd64                             1.0.27-1                                      amd64        API library for scanners
ii  sane-utils                                 1.0.27-1                                      amd64        API library for scanners -- utilities
ii  xsane                                      0.999-5ubuntu2                                amd64        featureful graphical frontend for SANE (Scanner Access Now Easy)
ii  xsane-common                               0.999-5ubuntu2                                all          xsane architecture independent files

```

**cat /etc/sane.d/dll.conf**
```
# dll.conf - Configuration file for the SANE dynamic backend loader
#
# Backends can also be enabled by configuration snippets under the dll.d/
# directory -- third party backends can drop their configuration file in
# this in this directory, named after the backend.
#
# The next line enables the network backend; comment it out if you don't
# need to use a remote SANE scanner over the network -- see sane-net(5)
# and saned(8) for details.
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
canon_dr
#canon_pp
cardscan
coolscan
#coolscan2
coolscan3
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
#epson
epson2
epsonds
fujitsu
#gphoto2
genesys
gt68xx
hp
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
kodak
kodakaio
kvs1025
kvs20xx
leo
lexmark
ma1509
magicolor
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
#p5
pie
pint
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
rts8891
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l
xerox_mfp
brother3
```

sudo scanimage -L
```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

**sudo sane-find-scanner**
```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x1164 [YUANRD], product=0x1f08 [STK7700D]) at libusb:002:004
found USB scanner (vendor=0x1c7a [Generic], product=0x0801 [FingerPrinter Reader]) at libusb:002:002
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x04f9 [Brother], product=0x023e [DCP-197C]) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

**groups**
```
cacodemon adm cdrom sudo dip plugdev lpadmin scanner saned sambashare
```

I can't understand where is the problem. Can you please help me?

Thanks in advance :)

---

