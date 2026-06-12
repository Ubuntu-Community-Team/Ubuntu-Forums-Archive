---
title: "USB2 Device Wont Work in USB3 Port"
date: 2011-09-15
forum: Hardware
---

### Post by wolke on 2011-09-15
i have a thinkpad w520 with 2 usb3 ports, a usb2 port, and an esata/usb2 port.

usb3 devices work beautifully in the usb3 ports at superspeed {100+ MB/s read/write}, and in the usb2 and esata/usb2 ports at usb2 speeds {~30 MB/s read/write}.

however, usb2 devices wont work in the usb3 port. heres the relevant dmesg:

```
[ 1856.830855] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1859.891108] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1862.961308] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1866.021555] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1866.021583] hub 3-0:1.0: unable to enumerate USB device on port 1

```

note that usb2 devices sometimes work in a usb3 port, if i connect a usb3 device into the other usb3 port. makes me think that this has something to do with over current detection.

---

### Post by wolke on 2011-09-15
heres the dmesg for plugging in a usb3 hard drive in the same usb3 port that wont work with my usb2 device, then mounting the disks, unmounting the disks, and removing the device.

that i see this once in awhile, every time:
  xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint

i get an 'unabled to enumerate' on every disconnect.
{also, running fsck now...}

```
[ 2360.500281] usb 4-1: new SuperSpeed USB device number 20 using xhci_hcd
[ 2360.518740] xhci_hcd 0000:0e:00.0: WARN: short transfer on control ep
[ 2360.519110] xhci_hcd 0000:0e:00.0: WARN: short transfer on control ep
[ 2360.519486] xhci_hcd 0000:0e:00.0: WARN: short transfer on control ep
[ 2360.519863] xhci_hcd 0000:0e:00.0: WARN: short transfer on control ep
[ 2360.521292] scsi19 : usb-storage 4-1:1.0
[ 2361.517938] scsi 19:0:0:0: Direct-Access     WD       My Book 3.0 1123 1006 PQ: 0 ANSI: 4
[ 2361.519106] sd 19:0:0:0: Attached scsi generic sg2 type 0
[ 2361.519151] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2361.520096] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2361.527442] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2361.528150] sd 19:0:0:0: [sdc] Spinning up disk....ready
[ 2371.138325] sd 19:0:0:0: [sdc] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[ 2371.138527] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2371.139041] sd 19:0:0:0: [sdc] Write Protect is off
[ 2371.139046] sd 19:0:0:0: [sdc] Mode Sense: 0a 00 10 00
[ 2371.139176] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2371.139746] sd 19:0:0:0: [sdc] No Caching mode page present
[ 2371.139751] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[ 2371.140332] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2371.140994] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2371.141495] sd 19:0:0:0: [sdc] No Caching mode page present
[ 2371.141500] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[ 2371.141872]  sdc: sdc1 sdc2 sdc3
[ 2371.142617] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2371.143225] xhci_hcd 0000:0e:00.0: WARN: Stalled endpoint
[ 2371.143728] sd 19:0:0:0: [sdc] No Caching mode page present
[ 2371.143733] sd 19:0:0:0: [sdc] Assuming drive cache: write through
[ 2371.143736] sd 19:0:0:0: [sdc] Attached SCSI disk
[ 2371.424728] EXT4-fs (sdc1): warning: maximal mount count reached, running e2fsck is recommended
[ 2371.428594] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[ 2371.438719] EXT4-fs (sdc2): warning: maximal mount count reached, running e2fsck is recommended
[ 2371.458598] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[ 2371.480109] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[ 2386.468919] usb 4-1: USB disconnect, device number 20
[ 2386.748983] hub 4-0:1.0: unable to enumerate USB device on port 1

```

---

### Post by wolke on 2011-09-15
forgot to say that the usb2 device works fine in usb2 ports as well.

heres the dmesg for plugging in the device that fails in usb3 {an n900} into a usb2 port, making it announce itself as an ethernet device {pc suite mode}, then disconnect the device.

```
[ 2864.926378] cdc_acm 2-1.2:1.6: This device cannot do calls on its own. It is not a modem.
[ 2864.926425] cdc_acm 2-1.2:1.6: ttyACM0: USB ACM device
[ 2864.927555] cdc_ether 2-1.2:1.8: usb0: register 'cdc_ether' at usb-0000:00:1d.0-1.2, CDC Ethernet Device, 42:c6:65:ac:8b:bd
[ 2942.114789] usb 2-1.2: USB disconnect, device number 6
[ 2942.229364] cdc_ether 2-1.2:1.8: usb0: unregister 'cdc_ether' usb-0000:00:1d.0-1.2, CDC Ethernet Device

```

---

### Post by wolke on 2011-09-15
for completeness, heres plugging the usb3 hd into a usb2 port. note the missing 'stalled's and the 'unable to enumerate'.

```
[ 3161.524759] usb 2-1.2: new high speed USB device number 13 using ehci_hcd
[ 3162.586365] scsi22 : usb-storage 2-1.2:1.0
[ 3163.585697] scsi 22:0:0:0: Direct-Access     WD       My Book 3.0 1123 1006 PQ: 0 ANSI: 4
[ 3163.586441] sd 22:0:0:0: Attached scsi generic sg2 type 0
[ 3163.589756] sd 22:0:0:0: [sdc] Spinning up disk....ready
[ 3171.606174] sd 22:0:0:0: [sdc] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[ 3171.606914] sd 22:0:0:0: [sdc] Write Protect is off
[ 3171.606920] sd 22:0:0:0: [sdc] Mode Sense: 0a 00 10 00
[ 3171.607663] sd 22:0:0:0: [sdc] No Caching mode page present
[ 3171.607667] sd 22:0:0:0: [sdc] Assuming drive cache: write through
[ 3171.610020] sd 22:0:0:0: [sdc] No Caching mode page present
[ 3171.610023] sd 22:0:0:0: [sdc] Assuming drive cache: write through
[ 3171.610545]  sdc: sdc1 sdc2 sdc3
[ 3171.613769] sd 22:0:0:0: [sdc] No Caching mode page present
[ 3171.613772] sd 22:0:0:0: [sdc] Assuming drive cache: write through
[ 3171.613775] sd 22:0:0:0: [sdc] Attached SCSI disk
[ 3171.931428] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[ 3171.992481] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[ 3172.026859] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[ 3180.489599] usb 2-1.2: USB disconnect, device number 13

```

---

### Post by wolke on 2011-11-09
bump

---

