---
title: "Modem: Intel Corporation 82801DB/DBL/DBM"
date: 2009-12-29
forum: Hardware
---

### Post by junovo on 2009-12-29
Hi 

Can anyone help me with finding the driver for the following modem.

Thanks 

--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009
 scanModem update of:  2009_12_26

The dialer utility package WVDIAL does not appear to be installed on your System. 
For Ubuntu users, there are at the bottom of [http://linmodems.technion.ac.il/packages/](http://linmodems.technion.ac.il/packages/)
packages with the files necessary to install wvdial, with names like: 
     wvdial_jaunty_amd64.zip   for x86_64, 64 bit bus systems.
     wvdial_jaunty_i386.zip    for 32 bit systems.
     wvdial_karmic_i386.zip    for 32 bit systems.
These are about 1 MB in size.  After downloaded and copied into your Linux partition:
$ unzip wv*.zip
Within the new folder:
$ sudo dpkg -i *.deb
will  complete the wvdial installation
Please read Modem/DOCs/wvdial.txt for usage information.

Presently install your Linux Distributions dkms package. It provides for automated driver updates,
following upgrade of your kernel.  For details see [http://linux.dell.com/projects.shtml#dkms](http://linux.dell.com/projects.shtml#dkms)

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
                  

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:1f.6, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:1f.6    8086:24c6    1014:0525    Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
 11:      62200    XT-PIC-XT        ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, eth1, yenta, yenta, Intel 82801DB-ICH4, eth0, radeon@pci:0000:01:00.0
 --- Bootup diagnostics for card in PCI slot 00:1f.6 ----
[    0.101980] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.101987] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.102026] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.102031] pci 0000:00:1f.6: PME# disabled
[    0.842888] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.842896] serial 0000:00:1f.6: PCI INT B disabled

---

