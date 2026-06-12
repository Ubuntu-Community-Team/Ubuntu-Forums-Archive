---
title: "SCSI CD Rewriter doesn't show"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by TheOnlyAardvark on 2006-03-25
I've got a SCSI CD-RW drive as secondary master on my dual-boot Win98SE/Ubuntu (Edubuntu) system. Works fine under 98SE.

The SCSI controller (Identified by Belarc Adviser under 98SE as an Adaptec AIC-7850 PCI SCSI Controller) shows up in the list when I use the 'lspci' command in terminal as 'AHA-7850', so I know Ubuntu sees it. Only thing is that Ubuntu doesn't see the CD-RW drive connected to the controller card.

Does anyone have any ideas how to get Ubuntu to 'see' my SCSI drive? Here is the result of 'lspci':

conor@edubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]

0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 47)

0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)

0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)

0000:00:0d.0 SCSI storage controller: Adaptec AHA-7850 (rev 01)

0000:00:0e.0 Network controller: AVM Audiovisuelles MKTG & Computer System GmbH A1 ISDN [Fritz] (rev 02)

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 65)
conor@edubuntu:~$

---

### Post by TheOnlyAardvark on 2006-03-31
Bump

---

