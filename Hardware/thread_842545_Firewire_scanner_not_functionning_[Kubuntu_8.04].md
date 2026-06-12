---
title: "Firewire scanner not functionning [Kubuntu 8.04]"
date: 2008-06-27
forum: Hardware
---

### Post by georgesgiralt on 2008-06-27
Hi !
I have an Epson 2450 Phot scanner.
When I plug it using firewire connection, it is seen :
```

[ 3362.564777] IEEE 1394 device has ROM CRC error
[ 3362.564914] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00004800001c613c]
[ 3362.567593] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 3362.709889] scsi6 : SBP-2 IEEE-1394
[ 3363.715117] ieee1394: sbp2: Logged into SBP-2 device
[ 3363.715364] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 3363.722321] scsi 6:0:0:0: Processor         EPSON    GT-9700          1.05 PQ: 0 ANSI: 4
[ 3363.722500] scsi 6:0:0:0: Attached scsi generic sg3 type 3
[ 3541.745080] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 3541.745097] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00004800001c613c]
[ 3564.400256] IEEE 1394 device has ROM CRC error
[ 3564.400294] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00004800001c613c]
[ 3564.400705] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 3564.541278] scsi7 : SBP-2 IEEE-1394
[ 3565.546453] ieee1394: sbp2: Logged into SBP-2 device
[ 3565.546687] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 3565.553775] scsi 7:0:0:0: Processor         EPSON    GT-9700          1.05 PQ: 0 ANSI: 4
[ 3565.553950] scsi 7:0:0:0: Attached scsi generic sg3 type 3

```
but neither Xsane nor Vuescan seen it. (xsane only list my webcam, and vuescan complains that "no scanner was found"
Any ideas, clues or leads ?
TIA !
P.S. when I plug it using USB, vuescan shows it but not Xsane. It is shown in the device selection window but Xsane is unable to acquire the preview nor scan.

---

### Post by phidia on 2008-06-27
The sane site is saying [your scanner]("http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=2450&bus=ieee&v=&p=") is working with 1394. Check out the links on that page and make sure you have the correct backend installed too (howtos are there at sane).

---

### Post by georgesgiralt on 2008-06-27
Thanks for your answer !
I *know* my scanner should work with Sane as I used it for years ! 
The things tha t puzzle me is that vuescan which is a self contained application does not see it as it should and has done before on different Linux variants.
I was wondering if there is something to check or configure regarding the Kubuntu Firewire stack ?
(the scanner work flawlessly on my desktop machine using Fedora 7 but with a different Ieee 1394 chipset, (from Texas Instruments I think) and as Fedora 7 reaches EOL support I was thinking migrating to Kubuntu.)

---

