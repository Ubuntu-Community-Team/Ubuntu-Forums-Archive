---
title: "Behringer X1204USB, not seeing the &quot;USB&quot; part working"
date: 2012-11-25
forum: Hardware
---

### Post by krystena on 2012-11-25
Editing this problem as "USB Soundcard" and "USB Audio Mixer" not being friendly. I managed to get the USB part working when I eliminated the USB soundcard, here is all the relevant information below for the topic now.. 

Output when USB Audio Mixer plugged in:
```

[ 8910.996144] usb 3-4: new full-speed USB device number 2 using xhci_hcd
[ 8911.015120] usb 3-4: ep 0x85 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 8911.019415] input: Burr-Brown from TI               USB Audio CODEC  as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.3/input/input18
[ 8911.019558] generic-usb 0003:08BB:2902.0005: input,hidraw4: USB HID v1.00 Device [Burr-Brown from TI               USB Audio CODEC ] on usb-0000:00:14.0-4/input3
[ 8916.751769] 5:4:3: usb_set_interface failed
[ 8916.752762] 5:3:1: usb_set_interface failed

```

lsusb -v (abridged for USB Mixer)
```

Bus 003 Device 003: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x08bb Texas Instruments Japan
  idProduct          0x2902 PCM2902 Audio Codec
  bcdDevice            1.00
  iManufacturer           1 Burr-Brown from TI              
  iProduct                2 USB Audio CODEC 
  iSerial                 0 
  bNumConfigurations      1

```

Ubuntu Precise, 64bit. Kernel 3.2.0-23.

---

### Post by krystena on 2012-11-25
Think I might have figured out the problem. I have a USB soundcard I'm using as well on top of this mixer, I like it as a headphone amp and again it did work in Windows 7 (whatever), but I think the two cards existing at the same time is a huge problem for this.

Not sure how to proceed other than removing my sound card and using the internal one that is meh, not what I wanna use. :/

This is the USB Soundcard, SB1240.
```

[15164.320479] usb 1-1.6: new full-speed USB device number 6 using ehci_hcd
[15164.439673] input: Creative Technology USB Sound Blaster HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.5/input/input20
[15164.439961] generic-usb 0003:041E:30D7.0007: input,hidraw2: USB HID v1.11 Device [Creative Technology USB Sound Blaster HD] on usb-0000:00:1a.0-1.6/input5


```
```

Bus 001 Device 007: ID 041e:30d7 Creative Technology, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x041e Creative Technology, Ltd
  idProduct          0x30d7 
  bcdDevice            1.00
  iManufacturer           1 Creative Technology
  iProduct                2 USB Sound Blaster HD
  iSerial                 3 00000AHT
  bNumConfigurations      1

```
More info 

this is pactl output for each card:

USB Soundcard
```

Sink #7
	State: RUNNING
	Name: alsa_output.usb-Creative_Technology_USB_Sound_Blaster_HD_00000AHT-00-HD.analog-stereo
	Description: USB Sound Blaster HD Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 48000Hz
	Channel Map: front-left,front-right
	Owner Module: 30
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor Source: alsa_output.usb-Creative_Technology_USB_Sound_Blaster_HD_00000AHT-00-HD.analog-stereo.monitor
	Latency: 26453 usec, configured 26000 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "4"
		alsa.card_name = "USB Sound Blaster HD"
		alsa.long_card_name = "Creative Technology USB Sound Blaster HD at usb-0000:00:1a.0-1.6, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:1a.0-usb-0:1.6:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/sound/card4"
		udev.id = "usb-Creative_Technology_USB_Sound_Blaster_HD_00000AHT-00-HD"
		device.bus = "usb"
		device.vendor.id = "041e"
		device.vendor.name = "Creative Technology, Ltd"
		device.product.id = "30d7"
		device.product.name = "USB Sound Blaster HD"
		device.serial = "Creative_Technology_USB_Sound_Blaster_HD_00000AHT"
		device.string = "front:4"
		device.buffering.buffer_size = "384000"
		device.buffering.fragment_size = "192000"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "USB Sound Blaster HD Analog Stereo"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB041e:30d7"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-usb"
	Ports:
		analog-output: Analog Output (priority: 9900)
	Active Port: analog-output
	Formats:
		pcm

```

USB Mixer
```

Sink #6
	State: SUSPENDED
	Name: alsa_output.usb-Burr-Brown_from_TI_USB_Audio_CODEC-00-CODEC.analog-stereo
	Description: PCM2902 Audio Codec Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 29
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor Source: alsa_output.usb-Burr-Brown_from_TI_USB_Audio_CODEC-00-CODEC.analog-stereo.monitor
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "USB Audio CODEC"
		alsa.long_card_name = "Burr-Brown from TI USB Audio CODEC at usb-0000:00:14.0-4, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:14.0-usb-0:4:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/sound/card1"
		udev.id = "usb-Burr-Brown_from_TI_USB_Audio_CODEC-00-CODEC"
		device.bus = "usb"
		device.vendor.id = "08bb"
		device.vendor.name = "Texas Instruments Japan"
		device.product.id = "2902"
		device.product.name = "PCM2902 Audio Codec"
		device.serial = "Burr-Brown_from_TI_USB_Audio_CODEC"
		device.string = "front:1"
		device.buffering.buffer_size = "352800"
		device.buffering.fragment_size = "176400"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "PCM2902 Audio Codec Analog Stereo"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB08bb:2902"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-usb"
	Ports:
		analog-output: Analog Output (priority: 9900)
	Active Port: analog-output
	Formats:
		pcm

```

Is there no way to use the USB mixer with the USB sound cards input? btw no, merely selecting the output to USB soundcard and input to USB mixer in the sound properties does NOT work, but it DOES work in Windows 7. Im not sure if perhaps the alsa.id is conflicting and if I can change it.

---

