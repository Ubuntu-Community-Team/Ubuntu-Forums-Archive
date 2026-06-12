---
title: "pci controller for NORCO DS-24E 24"
date: 2013-09-20
forum: Hardware
---

### Post by hendrikwout on 2013-09-20
Hi,

We are considering buying a NORCO DS-24E 24 3.5" Drive Bay for large storage capacity, see eg. [http://www.newegg.com/Product/Product.aspx?Item=N82E16816133047](http://www.newegg.com/Product/Product.aspx?Item=N82E16816133047).

We are wondering whether this can work with a server running ubuntu 12.04 or later. Note that the bay has an internal expander to host 24 hard drives with a single SFF-8088 mini-sas cable. Is there any Ubuntu-compatible pci controller which can deal with this storage system, preferably from Dell? At this moment, we've found the following controller: Dell 12DNW 6Gbps SAS HBA 8-Port External PCI-Express SAS Controller Card (see eg. [http://www.scsi4me.com/dell-012dnw-8-port-external-pci-express-6gbps-sas-hba-controller-card-with-2x-sff-8088-connectors.html](http://www.scsi4me.com/dell-012dnw-8-port-external-pci-express-6gbps-sas-hba-controller-card-with-2x-sff-8088-connectors.html)) . It seems it has support and drivers for some versions of redhat entreprise and suse, but I'm quite suspicious that it won't work with Ubuntu (or any Debian based system) due to lack of drivers.

Any ideas? Thanks in advance.
Hendrik

---

### Post by hendrikwout on 2014-02-23
Hi again,

For those who are interested in putting together a large storage workstation.... We took the risk and bought the storage hardware configuration for our workstation running ubuntu 13.10. Everything just works flawlessly out of the box already for a couple of months by mounting 4TB western digital SATA disks. Be warned... the fans in the NORCO DS-24E 24 3.5" make just an immense amount of noise. Don't forget to order an SFF-8088 cable for connecting the Norco with the sas controller.

Kind regards,
Hendrik

---

