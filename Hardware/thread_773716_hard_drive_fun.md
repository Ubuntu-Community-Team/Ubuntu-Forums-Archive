---
title: "hard drive fun"
date: 2008-04-29
forum: Hardware
---

### Post by survient on 2008-04-29
external hard drive is makin some funky noises, plugged it in, can no longer mount it, ran dmesg and here's what I get:
```

[ 8934.353914] usb 2-5: new high speed USB device using ehci_hcd and address 7
[ 8934.691504] usb 2-5: configuration #1 chosen from 1 choice
[ 8934.765075] usbcore: registered new interface driver libusual
[ 8934.793566] Initializing USB Mass Storage driver...
[ 8934.795758] scsi10 : SCSI emulation for USB Mass Storage devices
[ 8934.797998] usbcore: registered new interface driver usb-storage
[ 8934.798006] USB Mass Storage support registered.
[ 8934.799326] usb-storage: device found at 7
[ 8934.799824] usb-storage: waiting for device to settle before scanning
[ 8939.803262] usb-storage: device scan complete
[ 8939.806489] scsi 10:0:0:0: Direct-Access     Seagate  FreeAgent Pro    400A PQ: 0 ANSI: 4
[ 8939.814607] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 8939.818231] sd 10:0:0:0: [sdb] Write Protect is off
[ 8939.818236] sd 10:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[ 8939.818238] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 8939.823337] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 8939.825958] sd 10:0:0:0: [sdb] Write Protect is off
[ 8939.825960] sd 10:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[ 8939.825962] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 8939.825964]  sdb: sdb1
[ 8948.543189] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 8948.543230] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 8978.657320] usb 2-5: reset high speed USB device using ehci_hcd and address 7
[ 8993.744474] usb 2-5: device descriptor read/64, error -110
[ 9008.932528] usb 2-5: device descriptor read/64, error -110
[ 9009.135327] usb 2-5: reset high speed USB device using ehci_hcd and address 7
[ 9024.222490] usb 2-5: device descriptor read/64, error -110
[ 9039.411538] usb 2-5: device descriptor read/64, error -110
[ 9039.614340] usb 2-5: reset high speed USB device using ehci_hcd and address 7
[ 9044.621541] usb 2-5: device descriptor read/8, error -110
[ 9049.728506] usb 2-5: device descriptor read/8, error -110
[ 9049.931380] usb 2-5: reset high speed USB device using ehci_hcd and address 7
[ 9054.938357] usb 2-5: device descriptor read/8, error -110
[ 9060.045331] usb 2-5: device descriptor read/8, error -110
[ 9060.146172] usb 2-5: USB disconnect, address 7
[ 9060.146544] scsi 10:0:0:0: Device offlined - not ready after error recovery
[ 9060.149166] scsi 10:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9060.149174] end_request: I/O error, dev sdb, sector 976772992
[ 9060.149177] Buffer I/O error on device sdb, logical block 122096624
[ 9060.149206] Buffer I/O error on device sdb, logical block 122096624
[ 9060.149239] Buffer I/O error on device sdb, logical block 122096644
[ 9060.149245] Buffer I/O error on device sdb, logical block 122096644
[ 9060.149257] Buffer I/O error on device sdb, logical block 0
[ 9060.149263] Buffer I/O error on device sdb, logical block 1
[ 9060.149269] Buffer I/O error on device sdb, logical block 0
[ 9060.149277] Buffer I/O error on device sdb, logical block 0
[ 9060.149287] Buffer I/O error on device sdb, logical block 122096645
[ 9060.149300] Buffer I/O error on device sdb, logical block 122096645
[ 9060.249049] usb 2-5: new high speed USB device using ehci_hcd and address 8
[ 9075.336195] usb 2-5: device descriptor read/64, error -110
[ 9086.657354] end_request: I/O error, dev fd0, sector 0
[ 9090.524254] usb 2-5: device descriptor read/64, error -110
[ 9090.727052] usb 2-5: new high speed USB device using ehci_hcd and address 9
[ 9098.828583] end_request: I/O error, dev fd0, sector 0
[ 9105.814212] usb 2-5: device descriptor read/64, error -110
[ 9111.056061] end_request: I/O error, dev fd0, sector 0
[ 9121.002264] usb 2-5: device descriptor read/64, error -110
[ 9121.205067] usb 2-5: new high speed USB device using ehci_hcd and address 10
[ 9123.227242] end_request: I/O error, dev fd0, sector 0
[ 9126.212270] usb 2-5: device descriptor read/8, error -110
[ 9131.319237] usb 2-5: device descriptor read/8, error -110
[ 9131.521914] usb 2-5: new high speed USB device using ehci_hcd and address 11
[ 9135.399528] end_request: I/O error, dev fd0, sector 0
[ 9135.399535] printk: 26 messages suppressed.
[ 9135.399538] Buffer I/O error on device fd0, logical block 0
[ 9136.529087] usb 2-5: device descriptor read/8, error -110
[ 9141.636055] usb 2-5: device descriptor read/8, error -110
[ 9147.570872] end_request: I/O error, dev fd0, sector 0
[ 9147.570880] Buffer I/O error on device fd0, logical block 0

```
any software sided suggestions or apps that could try to do a repair? This drive won't even show up in gnome's partition editor. Thanks

---

### Post by tikey on 2008-08-13
I probably have a similar problem. (see [http://ubuntuforums.org/showthread.php?t=888557](http://ubuntuforums.org/showthread.php?t=888557))
I tried solving it by removing ehci_hcd
```
sudo modprobe -r ehci_hcd
```
but now I get
```
[ 7263.725600] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 7279.559570] usb 1-1: device descriptor read/64, error -110
[ 2735.801741] usb 1-1: device descriptor read/64, error -110
[ 2736.017560] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 7314.238213] usb 1-1: device descriptor read/64, error -110
[ 7334.140182] usb 1-1: device descriptor read/64, error -110
[ 2750.423311] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 7348.456412] usb 1-1: device not accepting address 7, error -110
[ 7348.568395] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 7362.926878] usb 1-1: device not accepting address 8, error -110

```

Did you find a solution for your problem or did you try anything else?

Thomas

---

### Post by Submatrix on 2008-08-13
Hello,

Does the HDD spin up and sound okay when you plug it in? if so, read on.

I had a similar problem and managed to get a fix. Because the terminal output suggested that the hard drive wasn't being recognised (as yours does) I figured that there couldn't be any problem with taking it apart and having a look.

When I removed the plastic casing there was a normal HDD, plugged into a little board which joined onto the drive's power and SATA ports. This board converts the SATA to USB and also tells the OS what the device is. It also pulls straight off. On the off chance that this board was the problem, I removed it and bought a [SATA to USB converter]("http://www.maplin.co.uk/Module.aspx?ModuleNo=48965&doy=13m8&C=SO&U=strat15") and plugged it straight into the drive. Connecting this up to the computer spun it up as usual and the drive was recognised and mounted with no problems.

Hope this helps

PS, if you decide to try this don't buy that one in the link I posted, they are available much more cheaply, that just happened to be the first hit in google

PPS, the drive in question was a WD passport

---

### Post by marioitalo on 2008-10-01
I found a solution to that problem (apparently this is about the time needed to the device wake-up):
At /etc/modprobe.d/options I added the line:
options scsi_mod inq_timeout=20
Then I tried to unload and load the module(scsi_mod), but didn't work, because this option was in initrd file. So I reinstalled the package linux-image-* what forced the system to make a new initrd file and use the new configuration (of course there is a better way to do that but I didn't want to search how to), then, after a reboot, voilá, the pen drive was back to life.:popcorn:
I hope this help someone.

---

