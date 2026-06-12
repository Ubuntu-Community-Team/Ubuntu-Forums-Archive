---
title: "No DisplayPort audio after 17.10 upgrade"
date: 2017-10-31
forum: Hardware
---

### Post by tyrion2323 on 2017-10-31
Dear Ubuntu Forums,

I am hoping that you all might be able to help me!

I recently upgraded from 17.04 Ubuntu Gnome to 17.10. After the upgrade, I found that I am unable to channel audio through my monitor, which worked fine before the upgrade. I am hoping that one of you might be able to help me out here. What can I do? I have attached useful information below.

**[SIZE=4]Some useful information[/SIZE]**
[LIST]
[*]I am using a Dell Ultrasharp 34-inch Ultrawide monitor with stereo speakers.
[*]The monitor is connected to a DisplayPort in my nVidia GTX 660Ti graphics card
[*]I am running Ubuntu 17.10, which was upgraded from Ubuntu Gnome 17.04
[/LIST]

**[SIZE=4]Steps I have taken[/SIZE]**
**[SIZE=2]Finding the card in PACMD[/SIZE]**
I have tried looking at the Pulse Audio configurer (pacmd), which detects the card and returns the following information. You can see that it under each output profile, it says: "available: no".
```
	name: <alsa_card.pci-0000_01_00.1>
	driver: <module-alsa-card.c>
	owner module: 6
	properties:
		alsa.card = "1"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xfb080000 irq 47"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.id = "0e0a"
		device.product.name = "GK104 HDMI Audio Controller"
		device.string = "1"
		device.description = "GK104 HDMI Audio Controller"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: no)
		output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: no)
		output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 300, available: no)
		output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: no)
		output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: no)
		output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: no)
		output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: no)
		output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: no)
		output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: no)
		output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 5200, available: no)
		output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Output (priority 100, available: no)
		output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Output (priority 100, available: no)
		off: Off (priority 0, available: unknown)
	active profile: <off>
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"
		hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"
		hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"
		hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "video-display"
```

**[SIZE=2]Finding the card using APLAY[/SIZE]**
I have also used aplay to detect the card. These are the results:

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: H [Logitech G933 Gaming Wireless H], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Finding the card using XRANDR
Again, XRANDR finds the card and indicates that it is outputting video via DisplayPort 1.
```
Screen 0: minimum 8 x 8, current 3440 x 1440, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected primary 3440x1440+0+0 (normal left inverted right x axis y axis) 798mm x 335mm
   3440x1440     59.97*+  49.99  
   2560x1440     59.95  
   2560x1080     60.00  
   1920x1080     60.00    60.00    59.94    50.00    60.00    50.04  
   1720x1440     60.00  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
```

**[SIZE=2]Using the Pulse Audio Volume Control GUI[/SIZE]**
When I use the Pulse Audio Volume Control GUI, I see the card represented; however, every profile listed under "GK104 HDMI Audio Controller" says "Unplugged".
[ATTACH=CONFIG]277362[/ATTACH]

---

