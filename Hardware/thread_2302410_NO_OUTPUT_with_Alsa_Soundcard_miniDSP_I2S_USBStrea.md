---
title: "NO OUTPUT with Alsa Soundcard miniDSP I2S USBStreamer"
date: 2015-11-10
forum: Hardware
---

### Post by kalexm on 2015-11-10
Hi,


I purchased a U-DAC 8 Soundcard at miniDSP: [https://www.minidsp.com/products/usb-audio-interface/u-dac8](https://www.minidsp.com/products/usb-audio-interface/u-dac8)
It is a combination of a USB to I2S/Toslink and an 8 Channel I2S DAC. Totally there are ten Input Channels and ten Output Channels.


It is USB XMOS chipset. It shall be USB2.0 along with the Audio Class 2.0.

It is recognized by Ubuntu - lsusb and aplay -l show the device.
I even managed to stream audio to the device: I created a ten channel whitenoise wav file S32_LE 44100 and managed to stream it using aplay to the device plughw:1,0 and hw:1,0.

But there is no sound on the RCA Jacks. I cross checked using OSX to verify that there is no hardware problem. On OSX there is sound.

Might be some kind of a mixer problem. For some funny reason the mixer shows only one input control and one output control. I did expect about ten controls.

The output of alsactl store looks like this:

```

[COLOR=black][FONT=&quot]state.USBStreamer{[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.1 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Playback Switch'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.0false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.1 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.2 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.3 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.4 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.5 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.6 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.7 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.8 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.9 [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type BOOLEAN[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 10[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.2 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Playback Switch'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]index 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type BOOLEAN[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.3 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Playback Volume'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.0 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.1 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.2 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.3 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.4 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.5 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.6 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.7 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.8 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.9 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type INTEGER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 10[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]range '0 - 255'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmin -12750[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmax 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.00[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.10[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.20[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.30[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.40[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.50[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.60[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.70[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.80[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.90[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.4 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Playback Volume'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]index 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type INTEGER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]range '0 - 255'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmin -12750[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmax 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.0 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.5 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value'USBStreamer Internal Clock'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type ENUMERATED[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]item.0'USBStreamer Internal Clock'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]item.1'USBStreamer TOSLINK Clock'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.6 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Capture Switch'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.0 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.1 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.2 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.3 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.4 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.5 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.6 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.7 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.8 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.9 true[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type BOOLEAN[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 10[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.7 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Capture Switch'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]index 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value false[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type BOOLEAN[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.8 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Capture Volume'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.0 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.1 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.2 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.3 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.4 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.5 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.6 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.7 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.8 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value.9 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type INTEGER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 10[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]range '0 - 255'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmin -12750[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmax 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.0 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.1 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.2 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.3 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.4 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.5 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.6 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.7 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.8 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.9 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]control.9 {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]iface MIXER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]name 'USBStreamerClock Selector Capture Volume'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]index 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]value 255[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]comment {[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]access 'readwrite'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]type INTEGER[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]count 1[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]range '0 - 255'[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmin -12750[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbmax 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]                     [/FONT][/COLOR][COLOR=black][FONT=&quot]dbvalue.0 0[/FONT][/COLOR]
[COLOR=black][FONT=&quot]              [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]       [/FONT][/COLOR][COLOR=black][FONT=&quot]}[/FONT][/COLOR]
[COLOR=black][FONT=&quot]}[/FONT][/COLOR]

```

I tried to find some information on the data-format but found nothing, so I have to guess. In this output there are a lot of playback channels, that are not shown in alsamixer. I tried to modify and set Value 0 -9 from false to true and restore this changed configuration. But it doesnt show the ten mixers afterwards neither.


My Question:


Why, and how do I have to modify this file to see all ten channels in alsamixer!?
Are the Channels muted?
Is it the problem or is there something else?

And besides these Questions: Is there a good alsa-documentation that dives in-depth?


```

~# uname -r
3.10.82-39

```


```

the kernel version is > 3.4
~# lsusb -s 3:5 -v


Bus 003 Device 005: ID 2752:0016  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x2752 
  idProduct          0x0016 
  bcdDevice            5.30
  iManufacturer           1 miniDSP 
  iProduct                2 USBStreamer 
  iSerial                 3 00001
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          441
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         3
      bFunctionClass          1 Audio
      bFunctionSubClass       0 
      bFunctionProtocol      32 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol     32 
      iInterface              2 USBStreamer 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               2.00
        bCategory               8
        wTotalLength          273
        bmControl            0x00
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype     10 (CLOCK_SOURCE)
        bClockID               41
        bmAttributes         0x03 Internal programmable Clock 
        bmControls           0x07
          Clock Frequency Control (read/write)
          Clock Validity Control (read-only)
        bAssocTerminal          0
        iClockSource            9 USBStreamer Internal Clock
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype     10 (CLOCK_SOURCE)
        bClockID               42
        bmAttributes         0x00 External Clock 
        bmControls           0x07
          Clock Frequency Control (read/write)
          Clock Validity Control (read-only)
        bAssocTerminal          0
        iClockSource           10 USBStreamer TOSLINK Clock
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype     11 (CLOCK_SELECTOR)
        bUnitID                40
        bNrInPins               2
        baCSourceID( 0)        41
        baCSourceID( 1)        42
        bmControls           0x03
          Clock Selector Control (read/write)
        iClockSelector          8 USBStreamer Clock Selector
      AudioControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bCSourceID             40
        bNrChannels            10
        bmChannelConfig   0x00000000
        bmControls    0x0000
        iChannelNames          15 I2S 0 Output L
        iTerminal               6 USBStreamer Output
      AudioControl Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      9 (EXTENSION_UNIT)
      Warning: Descriptor too short
        bUnitID                51
        wExtensionCode          0
        bNrPins                 1
        baSourceID( 0)          2
        bNrChannels            10
        wChannelConfig          0
        iChannelNames           3 00001
        bmControls        0x00
        iExtension             50 I2S 8 Input R
      AudioControl Interface Descriptor:
        bLength                50
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                10
        bSourceID              51
        bmaControls( 0)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 1)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 2)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 3)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 4)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 5)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 6)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 7)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 8)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 9)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls(10)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            20
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID              10
        bCSourceID             40
        bmControls         0x0000
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bCSourceID             40
        bNrChannels            10
        bmChannelConfig   0x00000000
        bmControls    0x0000
        iChannelNames          33 I2S 0 Input L
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      9 (EXTENSION_UNIT)
      Warning: Descriptor too short
        bUnitID                52
        wExtensionCode          0
        bNrPins                 1
        baSourceID( 0)          1
        bNrChannels            10
        wChannelConfig          0
        iChannelNames           3 00001
        bmControls        0x00
        iExtension             50 I2S 8 Input R
      AudioControl Interface Descriptor:
        bLength                50
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                11
        bSourceID              52
        bmaControls( 0)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 1)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 2)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 3)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 4)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 5)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 6)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 7)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 8)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 9)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls(10)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            22
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID              11
        bCSourceID             40
        bmControls         0x0000
        iTerminal               7 USBStreamer Input
      AudioControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      9 (EXTENSION_UNIT)
      Warning: Descriptor too short
        bUnitID                50
        wExtensionCode          0
        bNrPins                 2
        baSourceID( 0)          2
        baSourceID( 1)          1
        bNrChannels            18
        wChannelConfig          0
        iChannelNames           3 00001
        bmControls        0x00
        iExtension             32 I2S 8 Output R
      AudioControl Interface Descriptor:
        bLength                32
        bDescriptorType        36
        bDescriptorSubtype      4 (MIXER_UNIT)
        bUnitID                60
        bNrPins                 1
        baSourceID( 0)         50
        bNrChannels             8
        bmChannelConfig    0x00000000
        iChannelNames          49 I2S 8 Input L
 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
        bmControls         00
        iMixer                 0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              4 USBStreamer Audio Out
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              4 USBStreamer Audio Out
      AudioStreaming Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bmControls           0x00
        bFormatType             1
        bmFormats         0x00000001
          PCM
        bNrChannels            10
        bmChannelConfig   0x00000000
        iChannelNames          15 I2S 0 Output L
      AudioStreaming Interface Descriptor:
        bLength                 6
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bSubslotSize            4
        bBitResolution         24
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
        AudioControl Endpoint Descriptor:
          bLength                 8
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bmControls           0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              8
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes           17
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              5 USBStreamer Audio In
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              5 USBStreamer Audio In
      AudioStreaming Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink          22
        bmControls           0x00
        bFormatType             1
        bmFormats         0x00000001
          PCM
        bNrChannels            10
        bmChannelConfig   0x00000000
        iChannelNames          33 I2S 0 Input L
      AudioStreaming Interface Descriptor:
        bLength                 6
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bSubslotSize            4
        bBitResolution         24
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
        AudioControl Endpoint Descriptor:
          bLength                 8
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bmControls           0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      1 
      iInterface             12 USBStreamer DFU
      Device Firmware Upgrade Interface Descriptor:
        bLength                             9
        bDescriptorType                    33
        bmAttributes                        7
          Will Not Detach
          Manifestation Tolerant
          Upload Supported
          Download Supported
        wDetachTimeout                    250 milliseconds
        wTransferSize                      64 bytes
        bcdDFUVersion                   1.10
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          441
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         3
      bFunctionClass          1 Audio
      bFunctionSubClass       0 
      bFunctionProtocol      32 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol     32 
      iInterface              2 USBStreamer 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               2.00
        bCategory               8
        wTotalLength          273
        bmControl            0x00
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype     10 (CLOCK_SOURCE)
        bClockID               41
        bmAttributes         0x03 Internal programmable Clock 
        bmControls           0x07
          Clock Frequency Control (read/write)
          Clock Validity Control (read-only)
        bAssocTerminal          0
        iClockSource            9 USBStreamer Internal Clock
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype     10 (CLOCK_SOURCE)
        bClockID               42
        bmAttributes         0x00 External Clock 
        bmControls           0x07
          Clock Frequency Control (read/write)
          Clock Validity Control (read-only)
        bAssocTerminal          0
        iClockSource           10 USBStreamer TOSLINK Clock
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype     11 (CLOCK_SELECTOR)
        bUnitID                40
        bNrInPins               2
        baCSourceID( 0)        41
        baCSourceID( 1)        42
        bmControls           0x03
          Clock Selector Control (read/write)
        iClockSelector          8 USBStreamer Clock Selector
      AudioControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bCSourceID             40
        bNrChannels            10
        bmChannelConfig   0x00000000
        bmControls    0x0000
        iChannelNames          15 I2S 0 Output L
        iTerminal               6 USBStreamer Output
      AudioControl Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      9 (EXTENSION_UNIT)
      Warning: Descriptor too short
        bUnitID                51
        wExtensionCode          0
        bNrPins                 1
        baSourceID( 0)          2
        bNrChannels            10
        wChannelConfig          0
        iChannelNames           3 00001
        bmControls        0x00
        iExtension             50 I2S 8 Input R
      AudioControl Interface Descriptor:
        bLength                50
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                10
        bSourceID              51
        bmaControls( 0)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 1)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 2)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 3)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 4)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 5)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 6)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 7)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 8)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 9)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls(10)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            20
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID              10
        bCSourceID             40
        bmControls         0x0000
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bCSourceID             40
        bNrChannels            10
        bmChannelConfig   0x00000000
        bmControls    0x0000
        iChannelNames          33 I2S 0 Input L
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      9 (EXTENSION_UNIT)
      Warning: Descriptor too short
        bUnitID                52
        wExtensionCode          0
        bNrPins                 1
        baSourceID( 0)          1
        bNrChannels            10
        wChannelConfig          0
        iChannelNames           3 00001
        bmControls        0x00
        iExtension             50 I2S 8 Input R
      AudioControl Interface Descriptor:
        bLength                50
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                11
        bSourceID              52
        bmaControls( 0)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 1)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 2)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 3)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 4)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 5)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 6)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 7)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 8)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls( 9)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        bmaControls(10)      0x0000000f
          Mute Control (read/write)
          Volume Control (read/write)
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID            22
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID              11
        bCSourceID             40
        bmControls         0x0000
        iTerminal               7 USBStreamer Input
      AudioControl Interface Descriptor:
        bLength                17
        bDescriptorType        36
        bDescriptorSubtype      9 (EXTENSION_UNIT)
      Warning: Descriptor too short
        bUnitID                50
        wExtensionCode          0
        bNrPins                 2
        baSourceID( 0)          2
        baSourceID( 1)          1
        bNrChannels            18
        wChannelConfig          0
        iChannelNames           3 00001
        bmControls        0x00
        iExtension             32 I2S 8 Output R
      AudioControl Interface Descriptor:
        bLength                32
        bDescriptorType        36
        bDescriptorSubtype      4 (MIXER_UNIT)
        bUnitID                60
        bNrPins                 1
        baSourceID( 0)         50
        bNrChannels             8
        bmChannelConfig    0x00000000
        iChannelNames          49 I2S 8 Input L
 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
        bmControls         00
        iMixer                 0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              4 USBStreamer Audio Out
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              4 USBStreamer Audio Out
      AudioStreaming Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bmControls           0x00
        bFormatType             1
        bmFormats         0x00000001
          PCM
        bNrChannels            10
        bmChannelConfig   0x00000000
        iChannelNames          15 I2S 0 Output L
      AudioStreaming Interface Descriptor:
        bLength                 6
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bSubslotSize            4
        bBitResolution         24
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
        AudioControl Endpoint Descriptor:
          bLength                 8
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bmControls           0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              8
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes           17
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Feedback
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              5 USBStreamer Audio In
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol     32 
      iInterface              5 USBStreamer Audio In
      AudioStreaming Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink          22
        bmControls           0x00
        bFormatType             1
        bmFormats         0x00000001
          PCM
        bNrChannels            10
        bmChannelConfig   0x00000000
        iChannelNames          33 I2S 0 Input L
      AudioStreaming Interface Descriptor:
        bLength                 6
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bSubslotSize            4
        bBitResolution         24
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
        AudioControl Endpoint Descriptor:
          bLength                 8
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bmControls           0x00
          bLockDelayUnits         2 Decoded PCM samples
          wLockDelay              8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      1 
      iInterface             12 USBStreamer DFU
      Device Firmware Upgrade Interface Descriptor:
        bLength                             9
        bDescriptorType                    33
        bmAttributes                        7
          Will Not Detach
          Manifestation Tolerant
          Upload Supported
          Download Supported
        wDetachTimeout                    250 milliseconds
        wTransferSize                      64 bytes
        bcdDFUVersion                   1.10
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
 
```


```

:~# amixer -D hw:USBStreamer contents
numid=5,iface=MIXER,name='USBStreamer Clock Selector'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'USBStreamer Internal Clock'
  ; Item #1 'USBStreamer TOSLINK Clock'
  : values=0
numid=6,iface=MIXER,name='USBStreamer Clock Selector Capture Switch'
  ; type=BOOLEAN,access=rw------,values=10
  : values=on,on,on,on,on,on,on,on,on,on
numid=7,iface=MIXER,name='USBStreamer Clock Selector Capture Switch',index=1
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=8,iface=MIXER,name='USBStreamer Clock Selector Capture Volume'
  ; type=INTEGER,access=rw---R--,values=10,min=0,max=255,step=0
  : values=255,255,255,255,255,255,255,255,255,255
  | dBminmax-min=-127.50dB,max=0.00dB
numid=9,iface=MIXER,name='USBStreamer Clock Selector Capture Volume',index=1
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=255,step=0
  : values=255
  | dBminmax-min=-127.50dB,max=0.00dB
numid=1,iface=MIXER,name='USBStreamer Clock Selector Playback Switch'
  ; type=BOOLEAN,access=rw------,values=10
  : values=off,off,off,off,off,off,off,off,off,off
numid=2,iface=MIXER,name='USBStreamer Clock Selector Playback Switch',index=1
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=3,iface=MIXER,name='USBStreamer Clock Selector Playback Volume'
  ; type=INTEGER,access=rw---R--,values=10,min=0,max=255,step=0
  : values=255,255,255,255,255,255,255,255,255,255
  | dBminmax-min=-127.50dB,max=0.00dB
numid=4,iface=MIXER,name='USBStreamer Clock Selector Playback Volume',index=1
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=255,step=0
  : values=255
  | dBminmax-min=-127.50dB,max=0.00dB
  
```


```

:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: odroidaudio [odroid-audio], device 0: i2s0-pri dummy-aif1-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: odroidaudio [odroid-audio], device 1: i2s-sec dummy-aif2-1 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USBStreamer [USBStreamer], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  
```


```

root@max2play:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: odroidaudio [odroid-audio], device 0: i2s0-pri dummy-aif1-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: odroidaudio [odroid-audio], device 1: i2s-sec dummy-aif2-1 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USBStreamer [USBStreamer], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


```

:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
dmixer
    DMixer for hw:0,0
default
plugdmixer
plugequal
    Equalizer for DMixer
equal
sysdefault:CARD=odroidaudio
    odroid-audio, 
    Default Audio Device
dmix:CARD=odroidaudio,DEV=0
    odroid-audio, 
    Direct sample mixing device
dmix:CARD=odroidaudio,DEV=1
    odroid-audio, 
    Direct sample mixing device
dsnoop:CARD=odroidaudio,DEV=0
    odroid-audio, 
    Direct sample snooping device
dsnoop:CARD=odroidaudio,DEV=1
    odroid-audio, 
    Direct sample snooping device
hw:CARD=odroidaudio,DEV=0
    odroid-audio, 
    Direct hardware device without any conversions
hw:CARD=odroidaudio,DEV=1
    odroid-audio, 
    Direct hardware device without any conversions
plughw:CARD=odroidaudio,DEV=0
    odroid-audio, 
    Hardware device with all software conversions
plughw:CARD=odroidaudio,DEV=1
    odroid-audio, 
    Hardware device with all software conversions
sysdefault:CARD=USBStreamer
    USBStreamer, USB Audio
    Default Audio Device
front:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    Front speakers
surround21:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    Direct sample mixing device
dsnoop:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    Direct sample snooping device
hw:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    Direct hardware device without any conversions
plughw:CARD=USBStreamer,DEV=0
    USBStreamer, USB Audio
    Hardware device with all software conversions



```

---

