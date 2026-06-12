---
title: "Audio problem, microphone does not work"
date: 2022-06-15
forum: Hardware
---

### Post by WHK on 2022-06-15
Hi, i have a MSI X570S and Ubuntu 22.04 LTS, output audio works only on motherboard plug, external plug does not work, the microphone does not work in motherboard or external plug.

In the configurations I have tried the two types of input: "Microphone - USB Audio" and "Digital input (S/PDIF) - USB Audio" but does not work. Something curious is that the audio input detection bar in the settings panel moves along with the music I play as if the device was in a loop, but it is not capable of obtaining audio from the physical microphone.

The data of my hardware using alsa-info: [http://alsa-project.org/db/?f=df4d1f6c126260eabc5f159e64cff37efa064a38](http://alsa-project.org/db/?f=df4d1f6c126260eabc5f159e64cff37efa064a38)

How can I find out where the problem is?, thanks.

---

### Post by TheFu on 2022-06-16
For USB microphones, 

```
$ pactl list short sources
0       alsa_output.pci-0000_0a_00.3.analog-stereo.monitor      module-alsa-card.c      s16le 2ch 44100Hz SUSPENDED
2       alsa_output.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo.monitor       module-alsa-card.c        s16le 2ch 44100Hz       SUSPENDED
3       **alsa_input.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo**        module-alsa-card.c        s16le 2ch 44100Hz       SUSPENDED

$ pacmd set-default-source **alsa_input.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo**
```

The record using whatever software you like.  There are CLI tools for that too, if you like this will record and encode to vorbis audio:
```
$ parec -d  **alsa_input.usb-Samson_Technologies_Samson_GoMic-00.analog-stereo** \ 
   | oggenc -b 192 -o foo.ogg --raw - 
```

I used BOLD to show the same device specified in each command.

You can use **pavucontrol**  if you want a GUI sound controller.

So, with a different USB microphone, .... 
```
$ pactl list short sources
0       alsa_output.pci-0000_0a_00.3.analog-stereo.monitor      module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
4       **alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo**       module-alsa-card.c       s16le 2ch 32000Hz       SUSPENDED
```

You can figure out the rest of the commands.

# Record from named device to .wav
```
$ parecord -d alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo  -r saved.file.wav
```
== Note how raw recording uses parec and saving to WAV uses parecord?

I have a slightly different MB and system, obviously, but it is a B450 with a Ryzen.  All the USB ports work that are connected.  I have 4 USB2 front-panel ports that aren't connected, but there are 2 USB3 and an eSATA port there, along with analog microphone and speaker jacks which work.

When it comes to USB issues, try different devices, different cables, and see if the port, the cable, or the device is the issue. Devices that have power jacks should be powered by an external power, not the USB port if there are any issues.  Sometimes front USB ports are a little hub and not all USB devices work correctly going through a USB hub.

---

### Post by WHK on 2022-06-17
Thanks, i try change the input interface using pacmd:

```

whk@machine:~cat /proc/asound/cardsds
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfce20000 irq 119
 1 [Audio          ]: USB-Audio - USB Audio
                      Generic USB Audio at usb-0000:2a:00.1-2, high speed
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfcc00000 irq 121
whk@machine:~$ lsusb
Bus 006 Device 002: ID 1058:25a1 Western Digital Technologies, Inc. Elements / My Passport
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1b1c:0c1c Corsair CORSAIR iCUE Commander CORE
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 1462:7d53 Micro Star International MYSTIC LIGHT 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 8087:0032 Intel Corp. AX210 Bluetooth
Bus 001 Device 003: ID 0db0:151f Micro Star International USB Audio
Bus 001 Device 005: ID 04d9:1503 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 004: ID 0458:0186 KYE Systems Corp. (Mouse Systems) Genius DX-120 Mouse
Bus 001 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
whk@machine:~$ pactl list short sources
1	alsa_output.usb-Generic_USB_Audio-00.analog-stereo.monitor	module-alsa-card.c	s16le 2ch 44100Hz	IDLE
2	alsa_input.usb-Generic_USB_Audio-00.analog-stereo	module-alsa-card.c	s16le 2ch 44100Hz	SUSPENDED
whk@machine:~$ pacmd set-default-source alsa_input.usb-Generic_USB_Audio-00.analog-stereo
whk@machine:~$ pactl list short sources
1	alsa_output.usb-Generic_USB_Audio-00.analog-stereo.monitor	module-alsa-card.c	s16le 2ch 44100Hz	RUNNING
2	alsa_input.usb-Generic_USB_Audio-00.analog-stereo	module-alsa-card.c	s16le 2ch 44100Hz	RUNNING
whk@machine:~$ parecord -d alsa_input.usb-Generic_USB_Audio-00.analog-stereo  -r saved.file.wav

```

But can not capture audio from microphone, but record internal audio (by example when play youtube).

- Motherboard microphone plug is not work.
- Frontal microphone plug is not work.
- When change output from gnome settings to hdmi audio does not work, the audio continues to play in the plug and not in the monitor.
- When I change the input or output from digital to analog or sinput it does not change at all.
- The strangest thing is that the microphone input captures the audio that is heard in the system as if it were the output, audacious records the audio from the desktop when it tries to monitor the microphone.
- When plugging or unplugging the microphone, the system detects this change and tries to change the audio input automatically, but it does not capture the microphone and the desktop continues to be heard.
- [COLOR=#333333][FONT=monospace]When plug headphone in frontal plug the gnome setting change automaticaly to the headphone item, but the sound play in speakers, not in headphone.

[/FONT][/COLOR][COLOR=#333333][FONT=monospace]With pavucontrol have same result, can not capture microphone selecting it, but o[/FONT][/COLOR][COLOR=#333333][FONT=monospace]n Audacity when capture Alsa + "USB Audio: #2 (hw: 1,2)" works fine but [/FONT][/COLOR]it sounds very slowly[COLOR=#333333][FONT=monospace], but can not set on gnome settings as default microphone input.[/FONT][/COLOR]

---

### Post by WHK on 2022-06-17
It seems to be a common problem with audio interfaces that include S/PDIF:

- [https://wiki.archlinux.org/title/PulseAudio/Troubleshooting#Simultaneous_output_to_multiple_sinks_on_the_same_sound_card_not_working](https://wiki.archlinux.org/title/PulseAudio/Troubleshooting#Simultaneous_output_to_multiple_sinks_on_the_same_sound_card_not_working)
- [https://wiki.archlinux.org/title/Advanced_Linux_Sound_Architecture/Troubleshooting#S/PDIF_output_does_not_work](https://wiki.archlinux.org/title/Advanced_Linux_Sound_Architecture/Troubleshooting#S/PDIF_output_does_not_work)
- [https://askubuntu.com/questions/1098666/iec958-s-pdif-not-working](https://askubuntu.com/questions/1098666/iec958-s-pdif-not-working)
- [https://askubuntu.com/questions/313544/spdif-input-not-working](https://askubuntu.com/questions/313544/spdif-input-not-working)
- [https://unix.stackexchange.com/questions/677207/no-sound-on-iec958-s-pdif-input-sound-card-usb-cm106](https://unix.stackexchange.com/questions/677207/no-sound-on-iec958-s-pdif-input-sound-card-usb-cm106)

I am finding out more about the issue, to see how to give it a better solution, since some components necessary to solve it are not available for ubuntu 22, such as the pavucontrol extended options. Is a 8 years problem without native solution by default!.

---

### Post by TheFu on 2022-06-17
Analog microphones have been hit and miss for me.  Some work, some don't.  This is the 3.5mm jack-types.
Generic USB microphones sometimes don't work. Don't know why.  In my LUG, we've been having our weekly meetings online for almost 3 yrs and recommend a few brand-name microphones and cameras.  Anyone who shows up with audio that doesn't work usually fixed it by getting one of the known-to-work webcams.

Consumers don't use S/PDIF for microphones.  That's an output format, not input, to my knowledge.  I've seen a few uses (today) that seemed to need an interface to amplify and convert the input.

22.04 is too new for me.  I've been considering moving to 20.04 about a year for my desktops.

---

### Post by WHK on 2022-06-17
Thanks TheFu, i found the solution: [https://askubuntu.com/questions/1344880/microphone-not-showing-up-as-input-device-in-settings-only-in-pavucontrol](https://askubuntu.com/questions/1344880/microphone-not-showing-up-as-input-device-in-settings-only-in-pavucontrol)

Input microphone is not detected automaticaly by incompatibility problem.

With Audacity the hw:1,2 works fine to capture microphone but the gnome settings does not dettect, i need force to dettect in pulse configurations.

First, need find what is hardware 1,2:

```
$ arecord -l
**** Lista de CAPTURE dispositivos hardware ****
tarjeta 1: Audio [USB Audio], dispositivo 0: USB Audio [USB Audio]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Audio [USB Audio], dispositivo 1: USB Audio [USB Audio #1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Audio [USB Audio], dispositivo 2: USB Audio [USB Audio #2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```

It's ok, now need add to pulseaudio dettection adding a new file into /etc/pulse/default.pa.d/user.pa for custom configuration with content:

```
load-module module-alsa-source device=hw:1,2
.ifexists module-udev-detect.so
```

And restart without sudo or root:

```
$ pulseaudio -k ; pulseaudio -D
```

Now in gnome settings appear new item in input list below microphone input called "USB Audio", this work as microphone. Now need how to:

- Increase the microphone volume.
- Set the hardware as default microphone when plug the the phisical microphone.
- Make the headphones work.

---

### Post by WHK on 2022-06-17
Ok, headphone and microphone works fine with this settings:

```

load-module module-alsa-sink device=hw:1,0
load-module module-alsa-sink device=hw:1,1
load-module module-alsa-source device=hw:1,2
load-module module-alsa-source device=hw:1,3
.ifexists module-udev-detect.so

```

When:

- Reaar headphone  : hw:1,0
- Front headphone : hw:1,1
- Front microphone   : hw:1,2
- Rear microphoe   : hw:1,3

I test it using aplay and arecord, this two commands are agnostic to gnome settigs and works directely with hardware id. By example, for play in frontal headphone:

```
aplay -D plughw:1,1 /usr/share/sounds/alsa/Front_Center.wav
```

I test with each hardware listed in "aplay -l" for output and "arecord -l" for input, when id is card id and device id is hw:id,id. Descibed here: [https://wiki.archlinux.org/title/Advanced_Linux_Sound_Architecture/Troubleshooting#HDMI_Output_does_not_work](https://wiki.archlinux.org/title/Advanced_Linux_Sound_Architecture/Troubleshooting#HDMI_Output_does_not_work)

Now need how to change automaticaly input when plug the microphone.

---

### Post by web-user on 2022-06-18
Once I had an audio problem with Gentoo. I tried everything &#8212; no result.

*Turned out I connected it to the wrong 3.5mm jack port* :o

---

### Post by Yellow Pasque on 2022-06-19
I'm guessing your motherboard needs this fixup to label the volume controls correctly:
[https://github.com/torvalds/linux/commit/5762f980ca10dcfe5eead7c40d1c34cae61f409b](https://github.com/torvalds/linux/commit/5762f980ca10dcfe5eead7c40d1c34cae61f409b)

> **TheFu said:**
> For USB microphones
I don't think it's a USB microphone. This motherboard uses the new Realtek ALC4080 codec, which uses a USB connection internally, but still has 3.5mm I/O jacks.

---

### Post by henrystivens on 2022-11-17
This thread save my day. I have same problem with the Z590 Aourus PRO AX and Ubuntu 22.04 with 5.15.0-53-generic Kernel.

---

