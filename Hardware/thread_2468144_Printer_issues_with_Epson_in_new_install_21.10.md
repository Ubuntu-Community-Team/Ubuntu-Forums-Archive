---
title: "Printer issues with Epson in new install 21.10"
date: 2021-10-19
forum: Hardware
---

### Post by roadrash on 2021-10-19
I have just done a clean install of Ubunu's latest 21.10 but after installing it I went into settings and added my Epson SX600FW which ubuntu automatically detected.
I sent a test page to the printer but it says job completed but the printer just keeps pumping outr page after page of blank sheets.
I removed the printer and this time downloaded & installed the official Epson drivers but get thge same result.
Never used to have these problem with earlier versions and it just installed the printer from settings no trouble.
Seems to be buggy now somewhere.  Please can someone help get my 21.10 setup working with my printer again?

---

### Post by axelmasok on 2021-10-19
Plug the Epson into the old distro where it worked and record the CUPS driver/wrappers that it used to successfully print.
Compare with the detection by 21.19.  Post results.

---

### Post by roadrash on 2021-10-20
Ive overwritten that old install but think it was 18.04.  I could run it from a live environment if that would work.  I had this same problem with the 20.04 version too and didnt use it on my laptop for that reason but I thought they would have had it sorted on this version.  Ubuntu used to be great for printer drivers and all I had to do was plug in any printer and it worked.  What has gone so wrong?
Where do I find the CUPS driver/wrappers you talk about?

---

### Post by roadrash on 2021-10-22
Please help someone as my laptop is no good when I cannot use my printer now.  I am having to put anything I need to print onto a usb stick and take it to my desktop (has Mint on it) to print things out.
I would like Ubuntu and would like to keep Ubuntu on my Laptop but if I cant get it working with a printer soon I will have to change to older Mint or Debian.  I print over wifi normally

I put forward a bug report and this was the output if it helps:

> ProblemType: Bug
DistroRelease: Ubuntu 21.10
Package: cups 2.3.3op2-7ubuntu2
ProcVersionSignature: Ubuntu 5.13.0-19.19-generic 5.13.14
Uname: Linux 5.13.0-19-generic x86_64
NonfreeKernelModules: wl
ApportVersion: 2.20.11-0ubuntu70
Architecture: amd64
CasperMD5CheckResult: pass
CurrentDesktop: ubuntu:GNOME
Date: Wed Oct 20 17:56:35 2021
InstallationDate: Installed on 2021-10-19 (1 days ago)
InstallationMedia: Ubuntu 21.10 "Impish Indri" - Release amd64 (20211012)
Lpstat: device for Stylus-SX600FW: dnssd://EPSON._printer._tcp.local/
Lsusb:
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 003: ID 1bcf:2c18 Sunplus Innovation Technology Inc. HD WebCam
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
MachineType: Acer Aspire E1-571
Papersize: a4
PpdFiles: Error: command ['fgrep', '-H', '*NickName', '/etc/cups/ppd/Stylus-SX600FW.ppd'] failed with exit code 2: grep: /etc/cups/ppd/Stylus-SX600FW.ppd: Permission denied
ProcKernelCmdLine: BOOT_IMAGE=/boot/vmlinuz-5.13.0-19-generic root=UUID=fe427a7e-bf0c-4b48-9f93-78b19efdbd36 ro quiet splash vt.handoff=7
SourcePackage: cups
UpgradeStatus: No upgrade log present (probably fresh install)
dmi.bios.date: 03/11/2013
dmi.bios.release: 2.15
dmi.bios.vendor: Insyde Corp.
dmi.bios.version: V2.15
dmi.board.asset.tag: Type2 - Board Asset Tag
dmi.board.name: EA50_HC_CR
dmi.board.vendor: Acer
dmi.board.version: Type2 - Board Version
dmi.chassis.type: 10
dmi.chassis.vendor: Insyde Corp.
dmi.chassis.version: V2.15
dmi.ec.firmware.release: 0.0
dmi.modalias: dmi:bvnInsydeCorp.:bvrV2.15:bd03/11/2013:br2.15:efr0.0:svnAcer:pnAspireE1-571:pvrV2.15:skuAspireE1-571_064B_V2.15:rvnAcer:rnEA50_HC_CR:rvrType2-BoardVersion:cvnInsydeCorp.:ct10:cvrV2.15:
dmi.product.family: Type1Family
dmi.product.name: Aspire E1-571
dmi.product.sku: Aspire E1-571_064B_V2.15
dmi.product.version: V2.15
dmi.sys.vendor: Acer

---

### Post by axelmasok on 2021-10-24
See mine for example.
The driver line shows CUPS+Gutenprint.

```
Description:	Canon MG3000 series COLOUR
Location:	
Driver:	Canon MG2900 series - CUPS+Gutenprint v5.2.11 (color)
Connection:	usb://Canon/MG3000%20series?serial=699E05&interface=1
Defaults:	job-sheets=none, none media=iso_a4_210x297mm sides=one-sided
```

Gutenprint from 5.2.4 support Epson SX600FW: [https://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/5.2.6/NEWS/view](https://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/5.2.6/NEWS/view)

Epson supplies a filter/wrapper - epson-escpr. It supports your printer.

From CUPS/Openprinting your printer is listed as working perfectly: [https://www.openprinting.org/printer/Epson/Epson-Stylus_SX600FW](https://www.openprinting.org/printer/Epson/Epson-Stylus_SX600FW)

Dummy adding yours to my CUPS install I see it listed as : 
Epson Stylus SX600FW - CUPS+Gutenprint v5.3.1 (en)

I'm certain that will work. If that doesn't work with that driver/wrapper, my next move would be to plug in via USB and try again. If it works then you are chasing a different issue.

Let's see what Driver and Connection details look like from your Linux Mint?

---

