---
title: "Mounting USB Mass Media Storage from Samsung Upstage Cell Phone"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by mrglimm on 2008-01-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/161953](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/161953) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've had a gander at quite a few relative posts but nothing really gets anywhere.  There is a bug report, Bug #161953 in udev (Ubuntu) but it doesn't quite get me there.  

phone NOT connected
#dmesg 

[ 2855.346657] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2855.609989] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2855.873329] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2856.136673] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2856.400020] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2856.663359] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2856.926710] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2857.190043] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2857.453383] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2857.716732] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2857.980073] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2858.243413] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2858.506753] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2858.770107] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2859.033437] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2859.296785] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2859.560125] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2859.823511] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2860.086813] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2860.314284] usb 3-2: USB disconnect, address 5
[ 2860.317646] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.317826] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.317971] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318138] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318148] scsi 3:0:0:0: [sdc] READ CAPACITY failed
[ 2860.318151] scsi 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2860.318158] scsi 3:0:0:0: [sdc] Sense not available.
[ 2860.318166] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318173] scsi 3:0:0:0: [sdc] Write Protect is off
[ 2860.318177] scsi 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2860.318180] scsi 3:0:0:0: [sdc] Assuming drive cache: write through
[ 2860.318188] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318206] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318232] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318241] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318251] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318256] scsi 3:0:0:0: [sdc] READ CAPACITY failed
[ 2860.318259] scsi 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2860.318265] scsi 3:0:0:0: [sdc] Sense not available.
[ 2860.318272] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318278] scsi 3:0:0:0: [sdc] Write Protect is off
[ 2860.318282] scsi 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2860.318284] scsi 3:0:0:0: [sdc] Assuming drive cache: write through
[ 2860.318317] scsi 3:0:0:0: rejecting I/O to dead device

Phone IS connected
#dmesg

[ 2859.560125] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2859.823511] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2860.086813] usb 3-2: reset full speed USB device using uhci_hcd and address 5
[ 2860.314284] usb 3-2: USB disconnect, address 5
[ 2860.317646] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.317826] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.317971] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318138] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318148] scsi 3:0:0:0: [sdc] READ CAPACITY failed
[ 2860.318151] scsi 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2860.318158] scsi 3:0:0:0: [sdc] Sense not available.
[ 2860.318166] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318173] scsi 3:0:0:0: [sdc] Write Protect is off
[ 2860.318177] scsi 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2860.318180] scsi 3:0:0:0: [sdc] Assuming drive cache: write through
[ 2860.318188] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318206] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318232] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318241] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318251] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318256] scsi 3:0:0:0: [sdc] READ CAPACITY failed
[ 2860.318259] scsi 3:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2860.318265] scsi 3:0:0:0: [sdc] Sense not available.
[ 2860.318272] scsi 3:0:0:0: rejecting I/O to dead device
[ 2860.318278] scsi 3:0:0:0: [sdc] Write Protect is off
[ 2860.318282] scsi 3:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 2860.318284] scsi 3:0:0:0: [sdc] Assuming drive cache: write through
[ 2860.318317] scsi 3:0:0:0: rejecting I/O to dead device
[10007.071349] usb 3-2: new full speed USB device using uhci_hcd and address 7
[10007.235958] usb 3-2: configuration #1 chosen from 1 choice
[10007.238959] cdc_acm 3-2:1.0: ttyACM0: USB ACM device
[10010.841865] usb 3-2: USB disconnect, address 7
[10012.338116] usb 3-2: new full speed USB device using uhci_hcd and address 8
[10012.561705] usb 3-2: configuration #1 chosen from 1 choice
[10012.564761] scsi4 : SCSI emulation for USB Mass Storage devices
[10012.564969] usb-storage: device found at 8
[10012.564972] usb-storage: waiting for device to settle before scanning
[10017.550277] usb-storage: device scan complete
[10017.554265] scsi 4:0:0:0: Direct-Access     Samsung  Mass Storage     2.31 PQ: 0 ANSI: 2
[10017.688746] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10017.952092] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10018.215442] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10018.478771] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10018.742117] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10019.009446] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10019.158214] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[10019.158274] sd 4:0:0:0: Attached scsi generic sg3 type 0
[10019.412466] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10019.675781] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10019.939120] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10020.202467] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10020.465817] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10020.729150] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10020.992496] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10021.255836] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10021.519173] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10021.782521] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10022.045862] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10022.309282] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10022.584566] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10022.847861] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10023.111196] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10023.374543] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10023.637885] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10023.901242] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10024.164578] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10024.427919] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10024.691261] usb 3-2: reset full speed USB device using uhci_hcd and address 8
[10024.954614] usb 3-2: reset full speed USB device using uhci_hcd and address 8

I have edited the /etc/udev/rules.d/65-persistent-storage.rules as suggested in the Bug response, but it's not working for me...  any Linux masters know how to approach this?

---

### Post by mrglimm on 2008-01-28
bumper

---

### Post by mrglimm on 2008-02-06
No Linux users own a Sprint Upstage?  :-(

---

### Post by dfacto on 2008-07-20
I am having this problem with the Samsung SPH-M520.  I have also tried the above fix and had no luck.

---

