---
title: "Scanner powers down when USB connected"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by gewitty on 2007-03-06
I have an Epson Perfection 1670 USB scanner, which worked perfectly when I first installed Ubuntu. However, this morning there was a power failure that crashed my machines. When I got Ubuntu up and running again, I noticed that the scanner power light was out, even though it was plugged in. After checking it over, I eventually disconnected the USB cable and to my surprise found that the power light came on immediately. When I plug the cable back in, off goes the light again.

It's too much of a coincidence to think that the power outage was not the cause of the problem. But has anyone got any ideas as to what has actually happened?

---

### Post by teaker1s on 2007-03-06
burnt switch contacts and power outages can cause fault voltages above normal. These commonly toast eprom chips.

---

### Post by gewitty on 2007-03-06
I tried a couple of reboots to see what happened. As the machine goes through its initial boot sequence, the power light on the scanner is on. It goes out as soon as Ubuntu begins to load.

The following are two lines from the system log. This is what was recorded when I plugged the scanner USB cable in:

Mar  6 16:21:35 dave-desktop kernel: [17179901.596000] usb 4-4: new high speed USB device using ehci_hcd and address 7
Mar  6 16:21:35 dave-desktop kernel: [17179901.732000] usb 4-4: configuration #1 chosen from 1 choice

There is an entry for the scanner shown in Device Manager under the USB 2.0 section. It's not particularly helpful, but what it says is as follows:

Vendor: Seiko Epson Corp.
Device: USB Vendor Specific Interface
Status: Status
Bus Type: USB Interface
Device Type: Unknown
Capabilities: Unknown

I'm wondering if there is any way to completely uninstall this item of hardware and then reinstall it, in case there has been corruption of the drivers.

---

### Post by teaker1s on 2007-03-06
epson scanners use either "sane" or from epson direct "iscan" maybe searching and completely removing sane with synaptic and reinstalling would help?

---

### Post by gewitty on 2007-03-06
I found libscan and removed then replaced it. This also seemed to delete xscan, so I reinstalled that too.

It didn't solve the problem, but the scanner is behaving a little differently now. The power light remains on through the initial machine boot sequence and goes out as soon as Ubuntu starts to load, as before. But now the main scanner tube is permanently lit!

I'm beginning to suspect that something may be screwed in the scanner itself. I'll try installing it on another PC to check.

---

### Post by gewitty on 2007-03-07
I just called Epson tech support and they ran me through some questions and checks which they think points to a software/drivers problem. I Googled the error message I keep getting and found a debug routine to run in terninal. The results of this are as follows:

dave@dave-desktop:~$ SANE_DEBUG_SNAPSCAN=255 xsane
[sanei_debug] Setting debug level of snapscan to 255.
[snapscan] sane_snapscan_init
[snapscan] sane_snapscan_init: Snapscan backend version 1.4.53
[snapscan] add_usb_device(libusb:004:008)
[snapscan] add_usb_device: Detected (kind of) an USB device
[snapscan] snapscani_usb_open(libusb:004:008)
[snapscan] add_usb_device: Checking if 0x04b8 is a supported USB vendor ID
[snapscan] snapscani_check_device()
[snapscan] mini_inquiry
[snapscan] snapscan_cmd
[snapscan] snapscani_usb_cmd(0,0xbfb78b1a,6,0xbfb78b24,0xbfb78b20 (36))
[snapscan] atomic_usb_cmd(0,0xbfb78b1a,6,0xbfb78b24,0xbfb78b20 (36))
[snapscan] usb_cmd(0,0xbfb78b1a,6,0xbfb78b24,0xbfb78b20 (36))
[snapscan] usb_cmd: cmdlen=6, datalen=0
[snapscan] usb_write: writing:  0x12 0x00 0x00 0x00 0x24 0x00
[snapscan] Written 6 bytes
[snapscan] usb_read: reading:  0xf9 0x00 0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Read 8 bytes
[snapscan] usb_read: reading:  0x06 0x00 0x02 0x02 0x49 0x00 0x00 0x00 0x45 0x50 ...
[snapscan] Read 36 bytes
[snapscan] usb_read: reading:  0xfb 0x00 0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Read 8 bytes
[snapscan] snapscani_check_device: Is vendor "EPSON" model "EPSON Scanner" a supported scanner?
[snapscan] snapscani_get_model_id(EPSON Scanner, 0, 2)
[snapscan] snapscani_get_model_id: looking up scanner for ID 0x04b8,0x011f.
[snapscan] snapscani_get_model_id: scanner identified
[snapscan] snapscani_check_device: Autodetected driver: Perfection 1670
[snapscan] snapscani_usb_close(0)
[snapscan] 1st read 3 write 1
[snapscan] snapscani_usb_cmd(0,0xbfb78b02,6,0x0,0x0 (0))
[snapscan] atomic_usb_cmd(0,0xbfb78b02,6,0x0,0x0 (0))
[snapscan] usb_cmd(0,0xbfb78b02,6,0x0,0x0 (0))
[snapscan] usb_cmd: cmdlen=6, datalen=0
[snapscan] usb_write: writing:  0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Written 6 bytes
[snapscan] usb_read: reading:  0xfb 0x00 0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Read 8 bytes
[snapscan] 2nd read 4 write 2
[snapscan] snapscani_init_device_structure()
[snapscan] sane_snapscan_get_devices (0xbfb79d48, 0)
[snapscan] sane_snapscan_open (libusb:004:008, 0xbfb7bba4)
[snapscan] find_device
[snapscan] sane_snapscan_open: Allocating 64512 bytes as scanner buffer.
[snapscan] sane_snapscan_open: allocated scanner structure at 0x8260648
[snapscan] open_scanner
[snapscan] snapscani_usb_open(libusb:004:008)
[snapscan] sane_snapscan_open: waiting for scanner to warm up.
[snapscan] wait_scanner_ready
[snapscan] test_unit_ready
[snapscan] snapscan_cmd
[snapscan] snapscani_usb_cmd(0,0xbfb7b9b6,6,0x0,0x0 (0))
[snapscan] atomic_usb_cmd(0,0xbfb7b9b6,6,0x0,0x0 (0))
[snapscan] usb_cmd(0,0xbfb7b9b6,6,0x0,0x0 (0))
[snapscan] usb_cmd: cmdlen=6, datalen=0
[snapscan] usb_write: writing:  0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Written 6 bytes
[snapscan] usb_read: reading:  0xfb 0x00 0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Read 8 bytes
[snapscan] sane_snapscan_open: performing scanner self test.
[snapscan] send_diagnostic
[snapscan] snapscan_cmd
[snapscan] snapscani_usb_cmd(0,0xbfb7ba20,6,0x0,0x0 (0))
[snapscan] atomic_usb_cmd(0,0xbfb7ba20,6,0x0,0x0 (0))
[snapscan] usb_cmd(0,0xbfb7ba20,6,0x0,0x0 (0))
[snapscan] sane_snapscan_open: self test passed.
[snapscan] inquiry
[snapscan] snapscan_cmd
[snapscan] snapscani_usb_cmd(0,0x8260678,6,0x8260df8,0x8260788 (120))
[snapscan] atomic_usb_cmd(0,0x8260678,6,0x8260df8,0x8260788 (120))
[snapscan] usb_cmd(0,0x8260678,6,0x8260df8,0x8260788 (120))
[snapscan] usb_cmd: cmdlen=6, datalen=0
[snapscan] usb_write: writing:  0x12 0x00 0x00 0x00 0x78 0x00
[snapscan] Written 6 bytes
[snapscan] usb_read: reading:  0xf9 0x00 0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Read 8 bytes
[snapscan] usb_read: reading:  0x06 0x00 0x02 0x02 0x49 0x00 0x00 0x00 0x45 0x50 ...
[snapscan] Read 120 bytes
[snapscan] usb_read: reading:  0xfb 0x00 0x00 0x00 0x00 0x00 0x00 0x00
[snapscan] Read 8 bytes
[snapscan] inquiry: exposure time: 0.0 ms
[snapscan] inquiry: ms per line: 0.000000
[snapscan] inquiry: G2R_DIFF: 0
[snapscan] inquiry: B2R_DIFF: 0
[snapscan] inquiry: Chroma offsets=0; Red=0, Green:=0, Blue=0
[snapscan] inquiry: hardware config = 0x00
[snapscan] inquiry: bits per pixel = 14
[snapscan] inquiry: pixels per scan line = 0
[snapscan] inquiry: bytes per scan line = 0
[snapscan] inquiry: number of scan lines = 0
[snapscan] inquiry: effective buffer size = 0 bytes, 0 lines
[snapscan] inquiry: expected total scan data: 0 bytes
[snapscan] Looking up 31
[snapscan] Downloading /usr/share/sane/snapscan/your-firmwarefile.bin
[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.
[snapscan] sane_snapscan_open: download_firmware command failed: Invalid argument
[snapscan] sane_snapscan_exit

This seems to confirm that the scanner is OK, but the last few lines indicate a problem, with sane_snapscan. I've tried to find the file 'your-firmwarefile.bin', but the snapscan directory is missing in the  /usr/share/sane/ path. All that is in the sane directory is an xsane and gt68xx directory. Can anyone suggest what I should do to fix this?

---

### Post by teaker1s on 2007-03-09
```
gksudo synaptic
```
search xsane and sane and completely remove- this option removes configuration files.
Then reinstall them.

---

