---
title: "Unstable USB port on IBM T42"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by mr_crimp on 2007-01-11
Hi,

I have an IBM T42 laptop which have worked perfectly since Ubuntu 4.10 until now (Edgy). For about 2 months ago I started to experience problems with my USB ports. I had problems with connecting my printer, usb flash drive, usb external harddrive and my Nikon camera, every thing except my mouse.

For instance if I plug in my camera it sometimes mount correct and then when I am browsing the camera with Nautilus it suddenly disconnect. Other times it wont mount at all. This behaviour is symptomatic for all my drive devices(flash drive, external harddrive and camera). The printer just doesn't work.

If I boot up in windows all the devices are working perfect, so I think the devices are ok.

Is is the output of dmesg (I don't know if I have pasted the right text from dmeg if not please tell me what you need and I will paste it.):
```
[17179900.752000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17179900.944000] usb 2-1: configuration #1 chosen from 1 choice
[17179901.428000] usbcore: registered new driver libusual
[17179901.544000] SCSI subsystem initialized
[17179901.548000] Initializing USB Mass Storage driver...
[17179901.548000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179901.548000] usbcore: registered new driver usb-storage
[17179901.548000] USB Mass Storage support registered.
[17179901.548000] usb-storage: device found at 3
[17179901.548000] usb-storage: waiting for device to settle before scanning
[17179906.548000] usb-storage: device scan complete
[17179906.660000] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[17179906.980000] usb 2-1: device descriptor read/64, error -84
[17179907.344000] usb 2-1: device descriptor read/64, error -84
[17179907.560000] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[17179907.832000] usb 2-1: device descriptor read/64, error -84
[17179908.264000] usb 2-1: device descriptor read/64, error -84
[17179908.480000] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[17179908.516000] usb 2-1: device descriptor read/8, error -84
[17179908.676000] usb 2-1: device descriptor read/8, error -84
[17179908.892000] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[17179908.936000] usb 2-1: failed to restore interface 0 altsetting 0 (error=-71)
[17179908.936000] usb 2-1: USB disconnect, address 3
[17179909.048000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[17179909.236000] usb 2-1: configuration #1 chosen from 1 choice
[17179909.236000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179909.240000] usb-storage: device found at 4
[17179909.240000] usb-storage: waiting for device to settle before scanning
[17179914.240000] usb-storage: device scan complete
[17179914.356000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179914.604000] usb 2-1: device descriptor read/64, error -84
[17179914.944000] usb 2-1: device descriptor read/64, error -84
[17179915.160000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179915.464000] usb 2-1: device descriptor read/64, error -84
[17179915.800000] usb 2-1: device descriptor read/64, error -84
[17179916.016000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179916.056000] usb 2-1: device descriptor read/8, error -84
[17179916.268000] usb 2-1: device descriptor read/8, error -84
[17179916.484000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179916.528000]   Vendor: NIKON     Model: NIKON DSC E4500   Rev: 1.00
[17179916.528000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179916.744000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179917.008000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179917.280000] usb 2-1: device descriptor read/64, error -84
[17179917.676000] usb 2-1: device descriptor read/64, error -84
[17179917.892000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179918.140000] usb 2-1: device descriptor read/64, error -84
[17179918.516000] usb 2-1: device descriptor read/64, error -84
[17179918.732000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179918.812000] usb 2-1: device descriptor read/8, error -84
[17179918.972000] usb 2-1: device descriptor read/8, error -84
[17179919.188000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179919.236000] SCSI device sda: 500736 512-byte hdwr sectors (256 MB)
[17179919.240000] sda: Write Protect is off
[17179919.240000] sda: Mode Sense: 18 00 00 08
[17179919.240000] sda: assuming drive cache: write through
[17179919.356000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179919.624000] usb 2-1: device descriptor read/64, error -84
[17179919.988000] usb 2-1: device descriptor read/64, error -84
[17179920.204000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179920.556000] usb 2-1: device descriptor read/64, error -84
[17179920.968000] usb 2-1: device descriptor read/64, error -84
[17179921.184000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179921.244000] usb 2-1: device descriptor read/8, error -84
[17179921.420000] SCSI device sda: 500736 512-byte hdwr sectors (256 MB)
[17179921.424000] sda: Write Protect is off
[17179921.424000] sda: Mode Sense: 18 00 00 08
[17179921.424000] sda: assuming drive cache: write through
[17179921.424000]  sda:<6>usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179921.940000] usb 2-1: device descriptor read/64, error -84
[17179922.284000] usb 2-1: device descriptor read/64, error -84
[17179922.500000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179922.784000] usb 2-1: device descriptor read/64, error -84
[17179923.144000] usb 2-1: device descriptor read/64, error -84
[17179923.360000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179923.416000] usb 2-1: device descriptor read/8, error -84
[17179923.716000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179923.936000] usb 2-1: device descriptor read/64, error -84
[17179924.288000] usb 2-1: device descriptor read/64, error -84
[17179924.504000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179924.764000] usb 2-1: device descriptor read/64, error -84
[17179925.168000] usb 2-1: device descriptor read/64, error -84
[17179925.384000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179925.460000] usb 2-1: device descriptor read/8, error -84
[17179925.636000] usb 2-1: device descriptor read/8, error -84
[17179925.852000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179926.012000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179926.272000] usb 2-1: device descriptor read/64, error -84
[17179926.696000] usb 2-1: device descriptor read/64, error -84
[17179926.912000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179927.148000] usb 2-1: device descriptor read/64, error -84
[17179927.488000] usb 2-1: device descriptor read/64, error -84
[17179927.704000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179927.756000] usb 2-1: device descriptor read/8, error -84
[17179927.928000] usb 2-1: device descriptor read/8, error -84
[17179928.144000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179928.304000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179928.572000] usb 2-1: device descriptor read/64, error -84
[17179928.920000] usb 2-1: device descriptor read/64, error -84
[17179929.136000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179929.404000] usb 2-1: device descriptor read/64, error -84
[17179929.736000] usb 2-1: device descriptor read/64, error -84
[17179929.952000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179930.000000] usb 2-1: device descriptor read/8, error -84
[17179930.148000] usb 2-1: device descriptor read/8, error -84
[17179930.364000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179930.528000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179930.796000] usb 2-1: device descriptor read/64, error -84
[17179931.144000] usb 2-1: device descriptor read/64, error -84
[17179931.360000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179931.636000] usb 2-1: device descriptor read/64, error -84
[17179931.956000] usb 2-1: device descriptor read/64, error -84
[17179932.172000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179932.228000] usb 2-1: device descriptor read/8, error -84
[17179932.388000] usb 2-1: device descriptor read/8, error -84
[17179932.604000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179932.764000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179933.064000] usb 2-1: device descriptor read/64, error -84
[17179933.404000] usb 2-1: device descriptor read/64, error -84
[17179933.620000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179933.900000] usb 2-1: device descriptor read/64, error -84
[17179934.316000] usb 2-1: device descriptor read/64, error -84
[17179934.532000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179934.620000] usb 2-1: device descriptor read/8, error -84
[17179934.824000] sd 1:0:0:0: SCSI error: return code = 0x70000
[17179934.824000] end_request: I/O error, dev sda, sector 0
[17179934.824000] Buffer I/O error on device sda, logical block 0
[17179934.940000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179935.168000] usb 2-1: device descriptor read/64, error -84
[17179935.540000] usb 2-1: device descriptor read/64, error -84
[17179935.756000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179936.052000] usb 2-1: device descriptor read/64, error -84
[17179936.392000] usb 2-1: device descriptor read/64, error -84
[17179936.608000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179936.680000] usb 2-1: device descriptor read/8, error -84
[17179936.872000] usb 2-1: device descriptor read/8, error -84
[17179937.088000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179937.248000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179937.488000] usb 2-1: device descriptor read/64, error -84
[17179937.824000] usb 2-1: device descriptor read/64, error -84
[17179938.040000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179938.328000] usb 2-1: device descriptor read/64, error -84
[17179938.700000] usb 2-1: device descriptor read/64, error -84
[17179938.916000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179938.960000] usb 2-1: device descriptor read/8, error -84
[17179939.108000] usb 2-1: device descriptor read/8, error -84
[17179939.324000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179939.484000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179939.756000] usb 2-1: device descriptor read/64, error -84
[17179940.112000] usb 2-1: device descriptor read/64, error -84
[17179940.328000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179940.616000] usb 2-1: device descriptor read/64, error -84
[17179941.036000] usb 2-1: device descriptor read/64, error -84
[17179941.252000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179941.336000] usb 2-1: device descriptor read/8, error -84
[17179941.500000] usb 2-1: device descriptor read/8, error -84
[17179941.716000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179941.876000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179942.116000] usb 2-1: device descriptor read/64, error -84
[17179942.440000] usb 2-1: device descriptor read/64, error -84
[17179942.656000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179942.884000] usb 2-1: device descriptor read/64, error -84
[17179943.260000] usb 2-1: device descriptor read/64, error -84
[17179943.476000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179943.532000] usb 2-1: device descriptor read/8, error -84
[17179943.664000] usb 2-1: device descriptor read/8, error -84
[17179943.880000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179943.936000]  unable to read partition table
[17179943.940000] sd 1:0:0:0: Attached scsi removable disk sda
[17179944.004000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179944.124000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179944.396000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179944.720000] usb 2-1: device descriptor read/64, error -84
[17179945.056000] usb 2-1: device descriptor read/64, error -84
[17179945.272000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179945.556000] usb 2-1: device descriptor read/64, error -84
[17179945.896000] usb 2-1: device descriptor read/64, error -84
[17179946.112000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179946.160000] usb 2-1: device descriptor read/8, error -84
[17179946.316000] usb 2-1: device descriptor read/8, error -84
[17179946.532000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179946.688000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179947.032000] usb 2-1: device descriptor read/64, error -84
[17179947.372000] usb 2-1: device descriptor read/64, error -84
[17179947.588000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179947.892000] usb 2-1: device descriptor read/64, error -84
[17179948.264000] usb 2-1: device descriptor read/64, error -84
[17179948.480000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179948.536000] usb 2-1: device descriptor read/8, error -84
[17179948.704000] usb 2-1: device descriptor read/8, error -84
[17179948.920000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179949.084000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179949.340000] usb 2-1: device descriptor read/64, error -84
[17179949.724000] usb 2-1: device descriptor read/64, error -84
[17179949.940000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179950.148000] usb 2-1: device descriptor read/64, error -84
[17179950.500000] usb 2-1: device descriptor read/64, error -84
[17179950.716000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179950.772000] usb 2-1: device descriptor read/8, error -84
[17179950.944000] usb 2-1: device descriptor read/8, error -84
[17179951.160000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179951.320000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179951.596000] usb 2-1: device descriptor read/64, error -84
[17179951.956000] usb 2-1: device descriptor read/64, error -84
[17179952.172000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179952.436000] usb 2-1: device descriptor read/64, error -84
[17179952.820000] usb 2-1: device descriptor read/64, error -84
[17179953.036000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179953.108000] usb 2-1: device descriptor read/8, error -84
[17179953.252000] usb 2-1: device descriptor read/8, error -84
[17179953.468000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179953.628000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179953.920000] usb 2-1: device descriptor read/64, error -84
[17179954.284000] usb 2-1: device descriptor read/64, error -84
[17179954.500000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179954.780000] usb 2-1: device descriptor read/64, error -84
[17179955.152000] usb 2-1: device descriptor read/64, error -84
[17179955.368000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179955.512000] usb 2-1: device descriptor read/8, error -84
[17179955.800000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179956.032000] usb 2-1: device descriptor read/64, error -84
[17179956.372000] usb 2-1: device descriptor read/64, error -84
[17179956.588000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179956.880000] usb 2-1: device descriptor read/64, error -84
[17179957.248000] usb 2-1: device descriptor read/64, error -84
[17179957.464000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179957.584000] usb 2-1: device descriptor read/8, error -84
[17179957.756000] usb 2-1: device descriptor read/8, error -84
[17179957.972000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179958.016000] sd 1:0:0:0: SCSI error: return code = 0x70000
[17179958.016000] end_request: I/O error, dev sda, sector 0
[17179958.016000] Buffer I/O error on device sda, logical block 0
[17179958.132000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179958.404000] usb 2-1: device descriptor read/64, error -84
[17179958.752000] usb 2-1: device descriptor read/64, error -84
[17179958.968000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179959.240000] usb 2-1: device descriptor read/64, error -84
[17179959.640000] usb 2-1: device descriptor read/64, error -84
[17179959.856000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179959.924000] usb 2-1: device descriptor read/8, error -84
[17179960.072000] usb 2-1: device descriptor read/8, error -84
[17179960.288000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179960.504000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179960.732000] usb 2-1: device descriptor read/64, error -84
[17179961.084000] usb 2-1: device descriptor read/64, error -84
[17179961.300000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179961.584000] usb 2-1: device descriptor read/64, error -84
[17179961.996000] usb 2-1: device descriptor read/64, error -84
[17179962.212000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179962.260000] usb 2-1: device descriptor read/8, error -84
[17179962.420000] usb 2-1: device descriptor read/8, error -84
[17179962.636000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179962.796000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179963.048000] usb 2-1: device descriptor read/64, error -84
[17179963.384000] usb 2-1: device descriptor read/64, error -84
[17179963.600000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179963.836000] usb 2-1: device descriptor read/64, error -84
[17179964.212000] usb 2-1: device descriptor read/64, error -84
[17179964.428000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179964.468000] usb 2-1: device descriptor read/8, error -84
[17179964.624000] usb 2-1: device descriptor read/8, error -84
[17179964.840000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179965.000000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179965.352000] usb 2-1: device descriptor read/64, error -84
[17179965.752000] usb 2-1: device descriptor read/64, error -84
[17179965.968000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179966.288000] usb 2-1: device descriptor read/64, error -84
[17179966.600000] usb 2-1: device descriptor read/64, error -84
[17179966.816000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179966.868000] usb 2-1: device descriptor read/8, error -84
[17179967.024000] usb 2-1: device descriptor read/8, error -84
[17179967.240000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179967.400000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179967.632000] usb 2-1: device descriptor read/64, error -84
[17179967.932000] usb 2-1: device descriptor read/64, error -84
[17179968.148000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179968.548000] usb 2-1: device descriptor read/64, error -84
[17179968.908000] usb 2-1: device descriptor read/64, error -84
[17179969.124000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179969.184000] usb 2-1: device descriptor read/8, error -84
[17179969.352000] usb 2-1: device descriptor read/8, error -84
[17179969.568000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179969.732000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179969.988000] usb 2-1: device descriptor read/64, error -84
[17179970.352000] usb 2-1: device descriptor read/64, error -84
[17179970.568000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179970.820000] usb 2-1: device descriptor read/64, error -84
[17179971.160000] usb 2-1: device descriptor read/64, error -84
[17179971.376000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179971.480000] usb 2-1: device descriptor read/8, error -84
[17179971.632000] usb 2-1: device descriptor read/8, error -84
[17179971.848000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179971.896000] sd 1:0:0:0: SCSI error: return code = 0x70000
[17179971.896000] end_request: I/O error, dev sda, sector 8
[17179971.896000] Buffer I/O error on device sda, logical block 1
[17179972.012000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179972.272000] usb 2-1: device descriptor read/64, error -84
[17179972.748000] usb 2-1: device descriptor read/64, error -84
[17179972.964000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179973.288000] usb 2-1: device descriptor read/64, error -84
[17179973.648000] usb 2-1: device descriptor read/64, error -84
[17179973.920000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179973.956000] usb 2-1: device descriptor read/8, error -84
[17179974.112000] usb 2-1: device descriptor read/8, error -84
[17179974.328000] usb 2-1: reset full speed USB device using uhci_hcd and address 4
[17179974.380000] usb 2-1: device descriptor read/8, error -84
[17179974.540000] usb 2-1: device descriptor read/8, error -84
[17179974.644000] usb 2-1: USB disconnect, address 4
[17179974.644000]  1:0:0:0: SCSI error: return code = 0x10000
[17179974.644000] end_request: I/O error, dev sda, sector 16
[17179974.644000] Buffer I/O error on device sda, logical block 2
[17179974.644000]  1:0:0:0: rejecting I/O to dead device
[17179974.644000] Buffer I/O error on device sda, logical block 3
[17179974.644000]  1:0:0:0: SCSI error: return code = 0x10000
[17179974.644000] end_request: I/O error, dev sda, sector 0
[17179974.644000] Buffer I/O error on device sda, logical block 0
[17179974.648000]  1:0:0:0: rejecting I/O to dead device
[17179974.756000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[17179975.008000] usb 2-1: device descriptor read/64, error -84
[17179975.356000] usb 2-1: device descriptor read/64, error -84
[17179975.572000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[17179975.808000] usb 2-1: device descriptor read/64, error -84
[17179976.192000] usb 2-1: device descriptor read/64, error -84
[17179976.408000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[17179976.492000] usb 2-1: configuration #1 chosen from 1 choice
[17179976.492000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179976.492000] usb-storage: device found at 7
[17179976.492000] usb-storage: waiting for device to settle before scanning
[17179981.492000] usb-storage: device scan complete
[17179981.496000]   Vendor: NIKON     Model: NIKON DSC E4500   Rev: 1.00
[17179981.496000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179981.500000] SCSI device sda: 500736 512-byte hdwr sectors (256 MB)
[17179981.616000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179981.840000] usb 2-1: device descriptor read/64, error -84
[17179982.200000] usb 2-1: device descriptor read/64, error -84
[17179982.416000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179982.784000] usb 2-1: device descriptor read/64, error -84
[17179983.112000] usb 2-1: device descriptor read/64, error -84
[17179983.328000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179983.376000] usb 2-1: device descriptor read/8, error -84
[17179983.536000] usb 2-1: device descriptor read/8, error -84
[17179983.752000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179983.912000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179984.068000] sda: Write Protect is off
[17179984.068000] sda: Mode Sense: 18 00 00 08
[17179984.068000] sda: assuming drive cache: write through
[17179984.184000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179984.344000] SCSI device sda: 500736 512-byte hdwr sectors (256 MB)
[17179984.460000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179984.716000] usb 2-1: device descriptor read/64, error -84
[17179985.120000] usb 2-1: device descriptor read/64, error -84
[17179985.336000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179985.660000] usb 2-1: device descriptor read/64, error -84
[17179986.144000] usb 2-1: device descriptor read/64, error -84
[17179986.360000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179986.404000] usb 2-1: device descriptor read/8, error -84
[17179986.588000] usb 2-1: device descriptor read/8, error -84
[17179986.804000] usb 2-1: reset full speed USB device using uhci_hcd and address 7
[17179986.880000] usb 2-1: device descriptor read/8, error -84
[17179987.060000] usb 2-1: device descriptor read/8, error -84
[17179987.164000] usb 2-1: USB disconnect, address 7
[17179987.164000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[17179987.164000]  printing eip:
[17179987.164000] c0246907
[17179987.164000] *pde = 3ec63067
[17179987.164000] Oops: 0000 [#1]
[17179987.164000] SMP 
[17179987.164000] Modules linked in: sg sd_mod usb_storage scsi_mod libusual arc4 ieee80211_crypt_wep af_packet ipv6 binfmt_misc rfcomm l2cap bluetooth nvram uinput radeon drm speedstep_centrino cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi ibm_acpi i2c_ec i2c_core hotkey dock dev_acpi container button battery asus_acpi ac nls_iso8859_1 nls_cp437 vfat fat nls_utf8 ntfs lp pcmcia irtty_sir sir_dev tsdev snd_intel8x0 snd_ac97_codec snd_ac97_bus ipw2200 ieee80211 ieee80211_crypt e1000 nsc_ircc usbhid yenta_socket rsrc_nonstatic pcmcia_core irda snd_pcm_oss snd_mixer_oss crc_ccitt psmouse evdev floppy parport_pc parport serio_raw snd_pcm snd_timer snd soundcore snd_page_alloc intel_agp agpgart hw_random pcspkr shpchp pci_hotplug ext3 jbd ehci_hcd uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk piix generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
```

Thank you for your help...

---

### Post by danage on 2007-01-17
there are known issues with thinkpads of the t4x series in which the usb ports break in a way they will only support usb 1.1. try the same port with different devices, if the usb 1.1 devices work, you know it's a hardware issue

---

