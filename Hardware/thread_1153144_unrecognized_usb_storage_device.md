---
title: "unrecognized usb storage device"
date: 2009-05-08
forum: Hardware
---

### Post by vidyadhara on 2009-05-08
Have a problem with a media player I am connecting to my ubuntu 8.04 machine. This device is from YES corporation. [www.iloveyes.net](www.iloveyes.net) digital media player YMP-91.

I think all of the relevant usb modules are loaded (from lsmod )

uhci_hcd
ohci_hcd
ehci_hcd
usbcore
usbstorage
usbhid 

etc

I have only a very vague understanding about what these different modules achieve. I never compiled a kernel / module and probably would not dare to do so unless under extreme duress.

I think I am able to get some info from dmesg as I attach and detach this device. No entry is being created under /dev/ directory. Obviously something is happening here. dont know what these messages mean.

I have two different sets of USB ports on my machine. one set directly attached to the motherboard, an old box, has usb 1.0 ports (i believe the uhci_hcd ports) and another set on a PCI extension slot for usb 2.0. there it is using ehci_hcd module.

In either case my device is not recognized. I dont see any /dev/sd* device created.

How can I get to use this device. It is partitioned as fat16 to the best of my knowledge 
here is the part of the messages from dmesg that seem to be relevant.

Thanks in advance for any help.

[ 6056.478525] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 6056.655408] usb 1-1: configuration #1 chosen from 1 choice
[ 6056.677069] scsi6 : SCSI emulation for USB Mass Storage devices
[ 6056.681613] usb-storage: device found at 6
[ 6056.681631] usb-storage: waiting for device to settle before scanning
[ 6061.678518] usb-storage: device scan complete
[ 6061.682523] scsi 6:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[ 6061.686470] scsi 6:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[ 6061.701449] sd 6:0:0:0: [sdb] 7878656 512-byte hardware sectors (4034 MB)
[ 6061.765593] usb 1-1: USB disconnect, address 6
[ 6061.766204] sd 6:0:0:0: [sdb] Write Protect is off
[ 6061.766214] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6061.766222] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6061.766581] sd 6:0:0:0: [sdb] READ CAPACITY failed
[ 6061.766589] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6061.766602] sd 6:0:0:0: [sdb] Sense not available.
[ 6061.766670] sd 6:0:0:0: [sdb] Write Protect is off
[ 6061.766678] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6061.766684] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6061.766874] sd 6:0:0:0: [sdb] READ CAPACITY failed
[ 6061.766881] sd 6:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6061.766891] sd 6:0:0:0: [sdb] Sense not available.
[ 6061.766957] sd 6:0:0:0: [sdb] Write Protect is off
[ 6061.766965] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6061.766971] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 6061.767092] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 6061.767216] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 6061.768617] sd 6:0:0:1: [sdc] READ CAPACITY failed
[ 6061.768633] sd 6:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6061.768645] sd 6:0:0:1: [sdc] Sense not available.
[ 6061.768715] sd 6:0:0:1: [sdc] Write Protect is off
[ 6061.768723] sd 6:0:0:1: [sdc] Mode Sense: 00 00 00 00
[ 6061.768731] sd 6:0:0:1: [sdc] Assuming drive cache: write through
[ 6061.768908] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[ 6061.769026] sd 6:0:0:1: Attached scsi generic sg3 type 0
[ 6167.497926] usb 4-4: new high speed USB device using ehci_hcd and address 3
[ 6167.632108] usb 4-4: configuration #1 chosen from 1 choice
[ 6167.652968] scsi7 : SCSI emulation for USB Mass Storage devices
[ 6167.668410] usb-storage: device found at 3
[ 6167.668427] usb-storage: waiting for device to settle before scanning
[ 6172.664868] usb-storage: device scan complete
[ 6172.666730] scsi 7:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[ 6172.668615] scsi 7:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[ 6172.684178] sd 7:0:0:0: [sdb] 7878656 512-byte hardware sectors (4034 MB)
[ 6172.805240] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[ 6172.864023] usb 4-4: USB disconnect, address 3
[ 6172.865957] sd 7:0:0:0: [sdb] Write Protect is off
[ 6172.865974] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6172.865983] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6172.866406] sd 7:0:0:0: [sdb] READ CAPACITY failed
[ 6172.866414] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6172.866427] sd 7:0:0:0: [sdb] Sense not available.
[ 6172.866496] sd 7:0:0:0: [sdb] Write Protect is off
[ 6172.866504] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6172.866511] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6172.866701] sd 7:0:0:0: [sdb] READ CAPACITY failed
[ 6172.866708] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6172.866717] sd 7:0:0:0: [sdb] Sense not available.
[ 6172.866783] sd 7:0:0:0: [sdb] Write Protect is off
[ 6172.866791] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6172.866798] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6172.866956] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 6172.867090] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 6172.867696] sd 7:0:0:1: [sdc] READ CAPACITY failed
[ 6172.867703] sd 7:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 6172.867768] sd 7:0:0:1: [sdc] Sense not available.
[ 6172.867870] sd 7:0:0:1: [sdc] Write Protect is off
[ 6172.867878] sd 7:0:0:1: [sdc] Mode Sense: 00 00 00 00
[ 6172.867885] sd 7:0:0:1: [sdc] Assuming drive cache: write through
[ 6172.868004] sd 7:0:0:1: [sdc] Attached SCSI removable disk
[ 6172.868100] sd 7:0:0:1: Attached scsi generic sg3 type 0

---

