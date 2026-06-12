---
title: "hp scanjet 200"
date: 2013-03-18
forum: Hardware
---

### Post by paolobenve on 2013-03-18
I've bought an hp scanjet scanner, which every vendor site says it works in linux, but I cannot get it working with ubuntu 12.10.

When I connect it I'm seeing in syslog:

Mar 18 23:25:35 paolo kernel: [11734.032023] usb 1-2: new high-speed USB device number 10 using ehci_hcd
Mar 18 23:25:35 paolo mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Mar 18 23:25:35 paolo kernel: [11734.176998] usb 1-2: New USB device found, idVendor=03f0, idProduct=1c05
Mar 18 23:25:35 paolo kernel: [11734.177004] usb 1-2: New USB device strings: Mfr=10, Product=11, SerialNumber=12
Mar 18 23:25:35 paolo kernel: [11734.177008] usb 1-2: Product: HP Scanjet 200
Mar 18 23:25:35 paolo kernel: [11734.177012] usb 1-2: Manufacturer: Hewlett-Packard
Mar 18 23:25:35 paolo kernel: [11734.177015] usb 1-2: SerialNumber: CN319A13RC05RX
Mar 18 23:25:35 paolo mtp-probe: bus: 1, device: 10 was not an MTP device

but

$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

and

$ sudo sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1c05 [HP Scanjet 200]) at libusb:001:010
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

What is the Pipe error it says?

Any hint how to get it working?

Thank you!

---

### Post by Diomas on 2013-04-08
paolobenve, where did you find info this scanjet 200 is supported by linux? I can't find any

---

### Post by cirobr on 2014-03-02
Can anyone indicate on if support in Ubuntu is in place, or a forecasted deadline for that? Thanks in advance.

---

### Post by marconbr on 2014-03-04
I'm also having trouble to get the HP Scanjet 200 to work in Ubuntu 13.10.

After  [COLOR=#000000]$ sudo sane-find-scanner [/COLOR], I've got this:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1c05 [HP Scanjet 200]) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel


I didn't get the same Pipe error as paolobenve, but still, the result is pretty much the same: the scanner simply doesn't work.

It seems so far that  sane doesn't have support for the device.

Do anyone have any other idea or alternative to go around this issue? It's really annoying to have to resource to a virtual machine running windows every time I need to scan anything.

---

