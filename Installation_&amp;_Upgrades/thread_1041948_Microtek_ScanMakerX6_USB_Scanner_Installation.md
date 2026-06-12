---
title: "Microtek ScanMakerX6 USB Scanner Installation"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by SneakPeak on 2009-01-17
Hi

I am trying to install a Microtek ScanMakerX6 USB Scanner.  I had this working on Kubuntu 6.10 but I cannot get it working under 8.10. I am very much a newbie so I find things a bit tricky.  I have been advised to try various things but nothing has worked so far.  These are the things I have done:

scanimage -L returns: (same result for user and superuser)

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

I have checked dll.conf located in ./etc/sane.d There is no # in front of microtek2.  There are #'s in front of everything else except net

lsmod |grep microtek returns:

microtek               14848  0
scsi_mod              155212  7 sbp2,microtek,usb_storage,sr_mod,sd_mod,sg,libata
usbcore               148848  11 snd_usb_audio,snd_usb_lib,gspca_zc3xx,gspca_main,microtek,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd

lsscsi returns:

[0:0:0:0]    disk    ATA      MAXTOR STM380211 3.AA  -
[4:0:0:0]    cd/dvd  TSSTcorp CD/DVDW SH-S162L TS06  -
[4:0:1:0]    cd/dvd  HL-DT-ST CD-RW GCE-8525B  1.01  -
[5:0:0:0]    disk    ATA      FUJITSU MPC3084A 6021  -
[5:0:1:0]    cd/dvd  HITACHI  DVD-ROM GD-2500  0101  -
[6:0:0:0]    disk    Seagate  FreeAgentDesktop 100F  -
[7:0:0:0]    disk    Generic  USB Storage-CFC  I20A  -
[7:0:0:1]    disk    Generic  USB Storage-SDC  I20A  -
[7:0:0:2]    disk    Generic  USB Storage-SMC  I20A  -
[7:0:0:3]    disk    Generic  USB Storage-MSC  I20A  -
[8:0:0:0]    scanner          Scanner 636A4    1.20  -

export SANE_DEBUG_DLL=3 followed by scanimage -L gives:

[sanei_debug] Setting debug level of dll to 3.
[dll] sane_init: SANE dll backend version 1.0.12 from sane-backends 1.0.19
[dll] add_backend: adding backend `epkowa'
[dll] add_backend: adding backend `microtek2'
[dll] add_backend: adding backend `hpaio'
[dll] add_backend: adding backend `net'
[dll] add_backend: adding backend `microtek2'
[dll] add_backend: `microtek2' is already there
[dll] sane_get_devices
[dll] load: searching backend `microtek2' in `/usr/lib/sane'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-microtek2.so.1'
[dll] init: initializing backend `microtek2'
[dll] load: searching backend `net' in `/usr/lib/sane'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-net.so.1'
[dll] init: initializing backend `net'
[dll] load: searching backend `hpaio' in `/usr/lib/sane'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-hpaio.so.1'
[dll] init: initializing backend `hpaio'
[dll] load: searching backend `epkowa' in `/usr/lib/sane'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-epkowa.so.1'
[dll] init: initializing backend `epkowa'
[dll] sane_get_devices: found 0 devices

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[dll] sane_exit: exiting
[dll] sane_exit: calling backend `microtek2's exit function
[dll] sane_exit: calling backend `net's exit function
[dll] sane_exit: calling backend `hpaio's exit function
[dll] sane_exit: calling backend `epkowa's exit function
[dll] sane_exit: finished

Any help would be appreciated

Sneaks

---

### Post by SneakPeak on 2009-01-18
bump

---

