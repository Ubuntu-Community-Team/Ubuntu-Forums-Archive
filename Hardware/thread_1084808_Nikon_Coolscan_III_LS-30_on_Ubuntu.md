---
title: "Nikon Coolscan III LS-30 on Ubuntu"
date: 2009-03-02
forum: Hardware
---

### Post by hzFVOW00pw on 2009-03-02
For everyone who's struggling to make an old Nikon Coolscan LS-30 work on Ubuntu.

The Coolscan is supported by the 'sane' scanner backend, but the main thing is to make sure that the driver for the SCSI controller card to which the Coolscan is connected is loaded at startup. On my system I needed to load the 'initio' kernel module for my controller.

First install libsane with Synaptic or install from the commandline:

```
sudo apt-get install libsane
```

To load the SCSI driver create an arbitrarily named textfile in /etc/modprobe.d and put the line

```
alias scsi_hostadapter initio
```

in the textfile, save it, and reboot, or load the driver from the command line with

```
modprobe initio
```

The exact line in the textfile may differ for controllers of other brands, but this is the way to load the driver.

After that you can use your Coolscan from any scanning application.

Now try to make your Coolscan work in Win XP and you will be suprised how easy the Ubuntu way actually is...

---

### Post by bialyikar on 2012-05-30
Does not work :/
Ubuntu 12.04 64bit
Nikon LS-30

I created the file **scsi-driver.conf** in "/etc/modprobe.d" containing "alias scsi_hostadapter initio."

> 
lsscsi -c
Host: scsi5 Channel: 00 Target: 02 Lun: 00
  Vendor: Nikon    Model: COOLSCANIII      Rev: 1.31
  Type:   Scanner                          ANSI SCSI revision: 02


The file "proc/scsi/scsi" I have all the equipment listed by the command lsscsi except the scanner. The file looks like this:
> 
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3200827AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SAMSUNG HD501LJ  Rev: CR10
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SAMSUNG HD103UJ  Rev: 1AA0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 02 Lun: 00
  Vendor: Nikon    Model: COOLSCANIII      Rev: 1.31
  Type:   Scanner                          ANSI  SCSI revision: 02
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GSA-4163B Rev: A106
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 01 Lun: 00
  Vendor: Compaq   Model: DVD-ROM DVD-116  Rev: 1.06
  Type:   CD-ROM                           ANSI  SCSI revision: 05


In "dev", I have a device: sg0, sg1, SG2, SG3, SG4, SG5.

The file "/etc/sane.d/coolscan3.conf" looks like this:
> 
# coolscan3.conf: sample configuration file for coolscan3 backend
#
# The following entrie checks for your scanner by manufacturer (SCSI)
# and by vendor and product ID (USB). This is what the backend does when
# no configuration file can be found.
#
auto

# You can also configure the backend for specific device files, but this
# should not normally be necessary (under Linux at least).
# Syntax for specific devices: <interface>:<device>
#
# For a SCSI scanner, uncomment and edit the following line:
#scsi:/dev/scanner
#
# For a USB scanner, uncomment and edit the following line:
#usb:/dev/usbscanner
#
# For an IEEE 1394 scanner, use the SBP2 protocol (under Linux, use the
# sbp2 kernel module), and your scanner will be handled as a SCSI device.


---

