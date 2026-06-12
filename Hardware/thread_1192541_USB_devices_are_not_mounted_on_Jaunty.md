---
title: "USB devices are not mounted on Jaunty"
date: 2009-06-20
forum: Hardware
---

### Post by atari130xe on 2009-06-20
Hello forum I have installed Jaunty on a friends PC and each time he plug his cell Phone (Sony Ericsson W380), a Digital camera (a Benq), etc. the system does no mount the device like in Intrepid and older versions, I don know whats going on, I wish someone could give me a tip to solve this annoying problem.
thanks in advance,

Here it is the info:
```
emiliano@emiliano-desktop:~$ dmesg | grep usb
[    0.627912] usbcore: registered new interface driver usbfs
[    0.627931] usbcore: registered new interface driver hub
[    0.627967] usbcore: registered new device driver usb
[    2.900092] usb usb1: configuration #1 chosen from 1 choice
[    2.900506] usb usb2: configuration #1 chosen from 1 choice
[    2.900811] usb usb3: configuration #1 chosen from 1 choice
[    2.901114] usb usb4: configuration #1 chosen from 1 choice
[    2.901453] usb usb5: configuration #1 chosen from 1 choice
[    2.901628] usbcore: registered new interface driver libusual
[    2.901664] usbcore: registered new interface driver usbserial
[    2.901690] usbcore: registered new interface driver usbserial_generic
[    2.901692] usbserial: USB Serial Driver core
[ 7836.188062] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 7836.410972] usb 4-2: configuration #1 chosen from 1 choice
[ 7836.531155] usbcore: registered new interface driver spca561
[34361.560041] usb 4-2: USB disconnect, address 2
[34366.676032] usb 4-2: new full speed USB device using uhci_hcd and address 3
[34366.975988] usb 4-2: configuration #2 chosen from 1 choice
[34367.036153] usbcore: registered new interface driver cdc_acm
[34367.211801] last sysfs file: /sys/devices/pci0000:00/0000:00:10.2/usb4/4-2/4-2:2.3/interface
[34367.211916]  [<c03bb942>] ? usb_probe_interface+0xa2/0x130
[34367.211932]  [<c03bada1>] ? usb_match_id+0x41/0x60
[34367.211967]  [<c03bbc0c>] ? usb_register_driver+0x7c/0x100
[34393.552045] usb 4-2: USB disconnect, address 3
emiliano@emiliano-desktop:~$
```

and system events:
```
Jun 16 19:32:12 emiliano-desktop kernel: [34361.560041] usb 4-2: USB disconnect, address 2
Jun 16 19:32:12 emiliano-desktop kernel: [34361.561617] gspca: disconnect complete
Jun 16 19:32:17 emiliano-desktop kernel: [34366.676032] usb 4-2: new full speed USB device using uhci_hcd and address 3
Jun 16 19:32:17 emiliano-desktop kernel: [34366.975988] usb 4-2: configuration #2 chosen from 1 choice
Jun 16 19:32:17 emiliano-desktop kernel: [34367.029206] cdc_acm 4-2:2.1: ttyACM0: USB ACM device
Jun 16 19:32:17 emiliano-desktop kernel: [34367.036153] usbcore: registered new interface driver cdc_acm
Jun 16 19:32:17 emiliano-desktop kernel: [34367.036158] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211794] *pde = 00000000 
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211806] Dumping ftrace buffer:
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211810]    (ftrace buffer empty)
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211812] Modules linked in: cdc_wdm(+) cdc_acm gspca_spca561 gspca_main videodev v4l1_compat pppoe pppox binfmt_misc via drm bridge stp bnep vboxnetflt vboxdrv video output input_polldev lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm ppdev snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse pcspkr serio_raw snd soundcore snd_page_alloc i2c_viapro via_agp agpgart shpchp parport_pc parport via_rhine mii floppy fbcon tileblit font bitblit softcursor
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211849] 
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211852] Pid: 16341, comm: modprobe Not tainted (2.6.28-11-generic #42-Ubuntu) P4M89-M7B
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211855] EIP: 0060:[<f7f515f5>] EFLAGS: 00010282 CPU: 0
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211859] EIP is at wdm_probe+0x165/0x410 [cdc_wdm]
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211861] EAX: 00000000 EBX: 00000800 ECX: f7f55600 EDX: f2baae00
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211864] ESI: f0d0e2e5 EDI: f0cfb840 EBP: f2bb1cf4 ESP: f2bb1ca8
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211866]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jun 16 19:32:18 emiliano-desktop kernel: [34367.211872]  f2bb1cb4 c01cf830 ebb62560 f2bb1cd8 c020c036 f2baae00 f2baae1c c020b87b
Jun 16 19:32:18 emiliano-desktop kernel: [34367.212100] ---[ end trace ed750ffe922ae5b1 ]---
Jun 16 19:32:44 emiliano-desktop kernel: [34393.552045] usb 4-2: USB disconnect, address 3
Jun 16 19:59:43 emiliano-desktop -- MARK --
```

---

