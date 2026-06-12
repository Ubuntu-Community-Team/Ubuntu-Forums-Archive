---
title: "Some hardware isn't working!"
date: 2009-03-12
forum: Hardware
---

### Post by drfsite on 2009-03-12
Hi,

I'm new to Ubuntu!

Currently I have a Dell Dimension 2350 (though I've upgraded just about every component except the motherboard and case), and I'm also dual-booting with Windows XP.

I got most of my hardware to work - such as my nVidia video card and HP printer.  But a couple things still refuse to work.

One is my Creative Xmod sound card.  It shows up in Ubuntu as "Xmod", but I can't get any output.  It works in Amarok, but nothing else.  I tried the suggestion they had [here]("http://www.leadfollowmove.com/archives/linux/ubuntu-feisty-and-a-creative-xmod-sound-card/attachment/asoundconf-configuring-the-systems-default-audio-card"), but it still won't work.

The other is my wireless Wi-Fi card.  I don't have Ethernet in my room, so I use a Linksys USB card to connect to my router.  The specific model number is WUSB11 v2.6.  I tried some CVS thing, but it still refuses to connect: it sees my wireless networks, I put in the WEP key, and it just pops back up 2 minutes later after not connecting.  Currently I'm using a wireless Ethernet bridge, though I'd prefer to get the wireless working if it's at all possible.

Thanks in advance if anyone knows how to fix either of these, I'm using the newest version (Intrepid), if that helps.

I also have some boot problems but I'll save those as I can force it to work manually, these hardware problems I can't fix at all.

---

### Post by Admiral Nesquick on 2009-03-13
Which version of Ubuntu are you using ? That link gives a solution for Feisty fawn, it's not going to work in Hardy Heron or Intrepid Ibex.

---

### Post by drfsite on 2009-03-13
Oh, as I said before I'm using Intrepid.

I guess that shows how much I don't know about Linux... That command worked fine (no errors or anything), it just didn't fix the problem.

Any ideas how to get my sound card working on Intrepid then?

And does this mean every time a new version comes out I'm gonna have to jump through hoops to keep my hardware working?

---

### Post by Admiral Nesquick on 2009-03-13
Is the creative xmod an external sound card ( i don't recall any internal hardware from creative with that name ). If so, please use this terminal command : **dmesg | grep -i usb** and post the output here. So, we can see if the xmod is really recognized.

But, for now, you can use your integrated sound chip. Until we've got this problem fixed.

---

### Post by drfsite on 2009-03-13
Yes, the Xmod is a USB sound card.

It's coming up with a ton of stuff, including a bunch of errors about a USB port 4 (not sure which that is, all my things are functional...)

[   44.578223] usbcore: registered new interface driver usbfs
[   44.578342] usbcore: registered new interface driver hub
[   44.590283] usbcore: registered new device driver usb
[   44.602623] USB Universal Host Controller Interface driver v3.0
[   44.603256] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   44.603674] usb usb1: configuration #1 chosen from 1 choice
[   44.603796] hub 1-0:1.0: USB hub found
[   44.705765] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   44.706120] usb usb2: configuration #1 chosen from 1 choice
[   44.706230] hub 2-0:1.0: USB hub found
[   44.809691] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   44.810064] usb usb3: configuration #1 chosen from 1 choice
[   44.810174] hub 3-0:1.0: USB hub found
[   44.913682] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   44.945242] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   44.957174] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.957455] usb usb4: configuration #1 chosen from 1 choice
[   44.957568] hub 4-0:1.0: USB hub found
[   45.640327] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   45.773257] usb 4-1: configuration #1 chosen from 1 choice
[   46.012160] usb 4-2: new high speed USB device using ehci_hcd and address 3
[   46.144218] usb 4-2: configuration #1 chosen from 1 choice
[   46.144698] hub 4-2:1.0: USB hub found
[   46.886873] usb 4-2.1: new high speed USB device using ehci_hcd and address 6
[   46.995104] usb 4-2.1: configuration #1 chosen from 1 choice
[   46.995574] hub 4-2.1:1.0: USB hub found
[   47.314242] usb 4-2.2: new high speed USB device using ehci_hcd and address 7
[   47.424845] usb 4-2.2: configuration #1 chosen from 1 choice
[   47.637896] usb 4-2.3: new high speed USB device using ehci_hcd and address 8
[   47.748002] usb 4-2.3: configuration #1 chosen from 1 choice
[   47.961424] usb 4-2.4: new full speed USB device using ehci_hcd and address 9
[   48.070910] usb 4-2.4: configuration #1 chosen from 1 choice
[   48.071584] usbcore: registered new interface driver libusual
[   48.078904] Initializing USB Mass Storage driver...
[   48.308947] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   48.458693] usb 2-1: configuration #1 chosen from 1 choice
[   48.700455] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   48.875089] usb 2-2: configuration #1 chosen from 1 choice
[   48.889985] scsi4 : SCSI emulation for USB Mass Storage devices
[   48.891086] usb-storage: device found at 2
[   48.891091] usb-storage: waiting for device to settle before scanning
[   51.904557] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   53.882074] usb-storage: device scan complete
[   54.804958] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   57.705228] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   60.605635] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   60.606346] scsi5 : SCSI emulation for USB Mass Storage devices
[   60.607687] usb-storage: device found at 7
[   60.607692] usb-storage: waiting for device to settle before scanning
[   60.607741] scsi6 : SCSI emulation for USB Mass Storage devices
[   60.608991] usbcore: registered new interface driver usb-storage
[   60.609081] USB Mass Storage support registered.
[   60.609277] usbcore: registered new interface driver hiddev
[   60.609441] usb-storage: device found at 8
[   60.609444] usb-storage: waiting for device to settle before scanning
[   60.610471] input: Creative Technology Ltd Creative Xmod as /devices/pci0000:00/0000:00:1d.7/usb4/4-2/4-2.4/4-2.4:1.3/input/input2
[   60.625594] input,hidraw0: USB HID v1.11 Device [Creative Technology Ltd Creative Xmod] on usb-0000:00:1d.7-2.4
[   60.643193] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input3
[   60.653513] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   60.653843] usbcore: registered new interface driver usbhid
[   60.653925] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   65.599417] usb-storage: device scan complete
[   65.599677] usb-storage: device scan complete
[   73.158669] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7211
[   73.158803] usbcore: registered new interface driver usblp
[   73.777007] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   73.951406] ndiswrapper: driver netusb (Linksys,11/12/2001,2.10.37.2037) loaded
[   74.160553] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   76.585470] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   76.853132] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   77.006537] usbcore: registered new interface driver ndiswrapper
[   77.007383] Modules linked in: dcdbas snd_usb_audio snd_usb_lib snd_hwdep snd_intel8x0 snd_ac97_codec ac97_bus usblp cx88_alsa tuner tea5767 tda8290 tuner_simple mt20xx tea5761 snd_seq_dummy snd_pcm_oss snd_mixer_oss evdev snd_pcm cx8802 cx8800 cx88xx ndiswrapper snd_seq_oss ir_common snd_seq_midi tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common videobuf_dma_sg snd_rawmidi videobuf_core btcx_risc snd_seq_midi_event nvidia(P) snd_seq snd_timer snd_seq_device iTCO_wdt iTCO_vendor_support i2c_i810 pcspkr snd soundcore i2c_algo_bit intel_agp snd_page_alloc shpchp pci_hotplug i2c_core agpgart ext3 jbd mbcache usbhid hid usb_storage sr_mod cdrom pata_acpi libusual sg sd_mod ata_piix b44 floppy pata_sil680 ata_generic ssb mii libata scsi_mod ehci_hcd uhci_hcd usbcore fbcon tileblit font bitblit softcursor fuse
[   77.021838] Modules linked in: dcdbas snd_usb_audio snd_usb_lib snd_hwdep snd_intel8x0 snd_ac97_codec ac97_bus usblp cx88_alsa tuner tea5767 tda8290 tuner_simple mt20xx tea5761 snd_seq_dummy snd_pcm_oss snd_mixer_oss evdev snd_pcm cx8802 cx8800 cx88xx ndiswrapper snd_seq_oss ir_common snd_seq_midi tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common videobuf_dma_sg snd_rawmidi videobuf_core btcx_risc snd_seq_midi_event nvidia(P) snd_seq snd_timer snd_seq_device iTCO_wdt iTCO_vendor_support i2c_i810 pcspkr snd soundcore i2c_algo_bit intel_agp snd_page_alloc shpchp pci_hotplug i2c_core agpgart ext3 jbd mbcache usbhid hid usb_storage sr_mod cdrom pata_acpi libusual sg sd_mod ata_piix b44 floppy pata_sil680 ata_generic ssb mii libata scsi_mod ehci_hcd uhci_hcd usbcore fbcon tileblit font bitblit softcursor fuse
[   77.034052] usbcore: registered new interface driver snd-usb-audio
[   86.648960] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   89.549355] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   92.449625] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   95.350032] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  113.379406] usb 4-2.2: reset high speed USB device using ehci_hcd and address 7
[  116.843250] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  119.747508] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  122.647790] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  125.548185] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  125.636058] usb 4-2.2: reset high speed USB device using ehci_hcd and address 7
[  126.734700] usb 4-2.2: reset high speed USB device using ehci_hcd and address 7
[  127.837355] usb 4-2.2: reset high speed USB device using ehci_hcd and address 7
[  128.912133] usb 4-2.2: reset high speed USB device using ehci_hcd and address 7
[  130.006596] usb 4-2.2: reset high speed USB device using ehci_hcd and address 7
[  131.129185] usb 4-2.2: reset high speed USB device using ehci_hcd and address 7
[  146.797494] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  149.701881] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  152.602287] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  155.502563] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  177.411154] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  180.311428] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  183.215819] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  186.116229] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  207.373509] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  210.273912] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  213.174192] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  216.074590] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  237.335877] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  240.248253] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  243.152646] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  246.052919] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  267.302390] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  270.206641] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  273.111017] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  276.015436] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  297.264606] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  300.165241] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  303.078619] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  305.977899] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  327.227023] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  330.135466] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  333.039855] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  335.944252] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  357.185629] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  360.105805] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  363.018318] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  365.918640] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  387.144067] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  390.044329] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  392.944603] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  395.845005] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  417.110471] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  420.014685] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  422.919078] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  425.819474] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  447.072919] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  449.981164] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  452.881434] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  455.781842] hub 4-2.1:1.0: Cannot enable port 4.  Maybe the USB cable is bad?

Can you make heads or tails of that?

---

### Post by Admiral Nesquick on 2009-03-14
Is the card connected to port 4 ? Try connecting it to an other port.

---

### Post by drfsite on 2009-03-14
How do I know which one is port 4?

My sound card is on a USB hub along with my external hard drives, and those hard drives show up fine.
In order the ports go: Mouse, Wi-Fi adapter, USB hub, Printer... and my printer also works so I seriously have no idea which one is port 4.  Unless it's one of the front ones, but those also work fine when I plug in a flash drive.

---

### Post by Admiral Nesquick on 2009-03-14
Try not connecting this to a USB hub. Try connecting it to a USB port on your laptop. 

If that doesn't work i fear you will have to report it on Launchpad. Or take a look here :

[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

They say that ALSA should support it. Maybe it is a regressive bug.

---

