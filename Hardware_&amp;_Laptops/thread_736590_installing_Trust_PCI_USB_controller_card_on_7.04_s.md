---
title: "installing Trust PCI USB controller card on 7.04 server"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by shambolic on 2008-03-26
i inherited a Trust usb card with four ports.  it doesn't look like the manufacturer puts out a linux driver ([http://www.trust.com/products/product_detail.aspx?item=13083&section=support](http://www.trust.com/products/product_detail.aspx?item=13083&section=support) ) but i was under the impression there should be sofware kicking around for it, given that it's a via chipset.
it shows up as follows using lspci -v:

02:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 66, IRQ 19
	Memory at 40100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

and lsmod shows the following:
lsmod
Module                  Size  Used by
via                    44160  0 
drm                    81044  1 via
agpgart                35528  1 drm
ipv6                  273344  26 
ext2                   66696  1 
fuse                   46612  1 
parport_pc             36644  1 
lp                     12324  0 
parport                36808  2 parport_pc,lp
ext3                  132872  1 
jbd                    59816  1 ext3
mbcache                 9604  2 ext2,ext3
sg                     35996  0 
sd_mod                 23300  5 
floppy                 59396  0 
ehci_hcd               34572  0 
uhci_hcd               25488  0 
3c59x                  46760  0 
mii                     6656  1 3c59x
usbcore               134408  3 ehci_hcd,uhci_hcd
ata_piix               15620  3 
ata_generic             9092  0 
libata                125848  2 ata_piix,ata_generic
scsi_mod              142220  3 sg,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


i get the impression it's the ehci_hcd bit that's important, but can't for the life of me figure out if i need any additional drivers, etc.  of course the good folks at Trust don't seem to be able to shed much light.  i was hoping to use the card to add a WD external hard drive (passport), which doesn't show up when plugged in to the usb 2 controller, but does when plugged into the usb 1.1 controller that's built in to the motherboard (along with the excruciating transfer rates that entails).

i'd be very grateful for any pointers from some of you more experienced ubunters if you could spare a moment.
many thanks

jay

---

