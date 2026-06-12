---
title: "Install Microtek/Scanport SQ 2030"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by fusionex on 2005-12-26
Hi All,

I've installed sane, xsane, ppscsi using sudo apt-get install.  However when I try to run sane or xsane the program loads, tries to detect my scanner and closes.  I guess it's not finding my scanner.

My scanner is connected to the parallel port and uses some kind of SCSI emulation to work.  On top of that I know that my printer is connected to the scanner, because the scanner takes up the parallel printer port.

I've seen at least one site where someone has claimed to have gotten this combination to work on linux.  My primary concern at the moment is just getting the scanner to work.  Thanks to anyone who can help.

---

### Post by daller on 2005-12-26
It's probably unsupported!

[http://sane-project.org/sane-mfgs.html#Z-MICROTEK](http://sane-project.org/sane-mfgs.html#Z-MICROTEK)

Use the ebay-patch! :)

---

### Post by fusionex on 2005-12-26
Hmm...before I resort to the "ebay patch," Here's some info I was able to get about my scanner.  Also, if you have a good working color scanner, can you recommend it to me so that I can use it with the ebay patch?

Here's the info about my scanner I got from Daller's link:

Manufacturer: Scanport
Model: SQ2030
Interface: 2030
Status: basic (means it works at least in the most important modes but quality is not perfect)
Backend: microtek2 (unmaintained)
Manpage: sane-microtek2

Here's some output from a debugging log file and messing around with my microtek2.conf:

[sanei_debug] Setting debug level of microtek2 to 30.
[microtek2] sane_init: Microtek2 (v0.96 build 200410042220) says hello...
[microtek2] parse_config_file: fp=0x80754f0
[microtek2] attach_one: name='/dev/scanner'
[microtek2] add_device_list: device='/dev/scanner'
[microtek2] attach: device='/dev/scanner'
[microtek2] scsi_inquiry: mi=0x80757f4, device='/dev/scanner'
[microtek2] scsi_inquiry: 'Invalid argument'
[microtek2] attach: 'Invalid argument'
[microtek2] attach_one: name='/dev/sge'
[microtek2] add_device_list: device='/dev/sge'
[microtek2] attach: device='/dev/sge'
[microtek2] scsi_inquiry: mi=0x8076c6c, device='/dev/sge'
[microtek2] scsi_inquiry: 'Invalid argument'
[microtek2] attach: 'Invalid argument'
[microtek2] sane_get_devices: local_only=0
[microtek2] attach: device='/dev/sge'
[microtek2] scsi_inquiry: mi=0x8076c6c, device='/dev/sge'
[microtek2] scsi_inquiry: 'Invalid argument'
[microtek2] attach: 'Invalid argument'
[microtek2] sane_get_devices: attach status 'Invalid argument'
[microtek2] attach: device='/dev/scanner'
[microtek2] scsi_inquiry: mi=0x80757f4, device='/dev/scanner'
[microtek2] scsi_inquiry: 'Invalid argument'
[microtek2] attach: 'Invalid argument'
[microtek2] sane_get_devices: attach status 'Invalid argument'
scanimage: no SANE devices found
[microtek2] sane_exit:
[microtek2] sane_get_devices: local_only=0
[microtek2] sane_get_devices: sd_list_freed
[microtek2] sane_exit: MICROTEK2 says goodbye.

Thanks for any help...

---

