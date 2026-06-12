---
title: "No sound on Desktop 22.10 with Asrock TRX40 Creator"
date: 2023-03-02
forum: Hardware
---

### Post by jordiinbound on 2023-03-02
Hi All, 

It seems there is problems with finding the right drivers with this motherboard.

The output audio shows the displayport output that come trhough my graphic cards, so no sound trhough the speakers.

I gess i have to tell linux it has to take the output audio from the motherboard card, but no clue on how to do that.

I listed the devices and there is the audio card
2e:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller

I'm reading about pulse audio but I don't know if I can direct the output to the card with commands and how.

Could anyone kindly help me with this?

Kind regards,
Jordi

---

### Post by him610 on 2023-03-03
RE: [https://www.asrock.com/mb/AMD/TRX40%20Creator/index.asp#Specification]("https://www.asrock.com/mb/AMD/TRX40%20Creator/index.asp#Specification")

Just some thoughts....
On the AsRock page,  for your TRX Creator MB, it lists for its audio chip,....> Audio- 7.1 CH HD Audio (Realtek ALC4050H+ALC1220)
Normally the drivers for the audio chips have few issues; however, the possibility of mis-configuration is fairly high. I have a couple of AsRock boards and never had any issues with sound.

To provide a little more information, how about showing us the results (between code tags) from the terminal command line....
 ```
inxi -Axx
```

Your results should look similar to this ....
```

hugh@h270m:~$ inxi -Axx
Audio:
  Device-1: Intel 200 Series PCH HD Audio vendor: ASRock
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:a2f0
  Device-2: NVIDIA GK208 HDMI/DP Audio driver: snd_hda_intel v: kernel
    pcie: speed: 2.5 GT/s lanes: 8 bus-ID: 01:00.1 chip-ID: 10de:0e0f
  Device-3: Logitech Webcam B500 type: USB driver: snd-usb-audio,uvcvideo
    bus-ID: 1-3:2 chip-ID: 046d:0807
  Sound Server-1: ALSA v: k5.19.0-32-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
  
```

---

### Post by him610 on 2023-03-03
I reread your first post, the lines,
> The output audio shows the displayport output that come trhough my graphic cards, so no sound trhough the speakers.
I gess i have to tell linux it has to take the output audio from the motherboard card, but no clue on how to do that. 
Yes, that is called configuration. I don't know which desktop environment (DE) you are using, but I can only talk you through with DE I use, XFCE.
If your is different, you may need someone else to help.
*pavucontrol* is the program used to configure the audio ins & outs. *pavucontrol* can be run from the command line. 

On the XFCE DE there is a panel at the top of the screen, off to the right there should be a widget that looks like a speaker. 
If you click on the speaker widget, a dropdown box should appear that shows volume controls for speakers and microphone, but between the two should show a line that will reflect how the audio is currently configured. If you hover over that line, you should see the all of your options which you can select the one you want. Mine shows two options - *Built in Audio...*; and *GK208 HDMI/DP...*  Mine is set on *Built In Audio ....* to output sound through my 3.5 mm audio plug for earphones. I do not use speakers.
At the bottom of the box, there should be a line that reads *Audio Mixer...* Click on that to bring up the pavucontrol

---

### Post by jordiinbound on 2023-03-04
Thanks so much him610, quite new on Linux but trying to learn as much as I can.

Here you are the inxi output
udio:
  Device-1: NVIDIA GA102 High Definition Audio vendor: ZOTAC
    driver: snd_hda_intel v: kernel pcie: speed: 16 GT/s lanes: 2
    bus-ID: 01:00.1 chip-ID: 10de:1aef
  Device-2: AMD Starship/Matisse HD Audio vendor: ASUSTeK driver: N/A pcie:
    speed: 16 GT/s lanes: 16 bus-ID: 2e:00.4 chip-ID: 1022:1487
  Device-3: NVIDIA GA102 High Definition Audio vendor: ZOTAC
    driver: snd_hda_intel v: kernel pcie: speed: 2.5 GT/s lanes: 8
    bus-ID: 41:00.1 chip-ID: 10de:1aef
  Sound Server-1: ALSA v: k5.19.0-35-generic running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes


In the speaker control I only have listed the Nvidia HDMI cards

How can I direct then the right sound device 2?

Thanks so much!
Jordi

---

### Post by jordiinbound on 2023-03-04
I also see the alsa controler only list one source (the one chosen in settings) which is not the moderboard one.

* index: 0
	name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: APPLICATION|IDLE
	priority: 1030
	volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Estèreo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 1999.82 ms
	monitor_of: 0
	card: 0 <alsa_card.pci-0000_01_00.1>
	module: 7
	properties:
		device.description = "Monitor of GA102 High Definition Audio Controller Digital Stereo (HDMI 2)"
		device.class = "monitor"
		alsa.card = "1"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xf5080000 irq 351"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.1/0000:01:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.id = "1aef"
		device.product.name = "GA102 High Definition Audio Controller"
		device.string = "1"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"

---

### Post by him610 on 2023-03-04
There is also a command line tool, *alsamixer*, that can be used to **select** and configure you sound chips along with the ins & outs. Looks like this...
[https://imgur.com/kV4fWMV.png]("https://imgur.com/kV4fWMV.png")

---

