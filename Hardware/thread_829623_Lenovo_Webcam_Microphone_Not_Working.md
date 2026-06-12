---
title: "Lenovo Webcam Microphone Not Working"
date: 2008-06-15
forum: Hardware
---

### Post by roadkillbunny on 2008-06-15
Hi there,
I am trying to get the built-in microphone of the Lenovo USB Webcam to work on Ubuntu Hardy Heron. The webcam itself works great (using the [GSPCA driver]("http://mxhaard.free.fr/index.html")), but I have no idea where to start on getting the microphone to work. First of all, the microphone is being identified by all the sound applications, however when I try to use it I get errors.

Below is some information about the things I tried to get it working.

Plugging in the camera, I see the following output in dmesg:
```
Jun 14 18:56:25 sein kernel: [13660.122359] usb 6-2: new high speed USB device using ehci_hcd and address 2
Jun 14 18:56:25 sein kernel: [13660.408259] usb 6-2: configuration #1 chosen from 1 choice
Jun 14 18:56:25 sein kernel: [13660.546357] Linux video capture interface: v2.00
Jun 14 18:56:25 sein kernel: [13660.561221] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0323) 
Jun 14 18:56:25 sein kernel: [13660.792293] usbcore: registered new interface driver gspca
Jun 14 18:56:25 sein kernel: [13660.792306] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Jun 14 18:56:25 sein kernel: [13660.830381] usbcore: registered new interface driver snd-usb-audio
Jun 14 18:56:27 sein pulseaudio[6778]: alsa-util.c: Cannot find fallback mixer control "Mic".
```

lsusb gives me this:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 17ef:4802 ChipsBnk 
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 17ef:1000 ChipsBnk 
Bus 001 Device 001: ID 0000:0000  
```

I see an entry "USB Audio" under Capture in the Ubuntu Sound Preferences, which I assume is the webcam mic, but when I press the test button I get the following error:
```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

I also see an entry in Volume Control, called *Lenovo USB Webcam (Also mixer)*. The entry has two tabs: Recording and Switches. The Recording tab has an PCM option which is turned to highest setting and the microphone icon at the bottom is enabled (that is there is no red X across it). In the Switches section I see "Auto Gain Control", which is checked.

Next I tried run arecord from command line to see if it is working, after all it is being detected. However playing back the recording gives no sound. Here is how I tested it:
```
kkrizka@sein:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Webcam [Lenovo USB Webcam], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kkrizka@sein:~$ arecord -c 1 -f cd > test.wav
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Aborted by signal Interrupt...
kkrizka@sein:~$ aplay test.wav 
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
kkrizka@sein:~$ 
```
No sound is being played back, but the aplay application runs for the amount of time I spent recording.

My final attempt was to see what happens when I try a test-call with Skype. In the sound-input I see two options to do with USB: Lenovo USB Webcam (hw:Webcam,0) and Lenovo USB Webcam (plughw:Webcam,0). When I try the first one, I get the following error on command line:
```
RtApiAlsa: callback thread error (RtApiAlsa: audio read error for device (Lenovo USB Webcam (hw:Webcam,0)): Input/output error.) ... closing stream.
```
With the second option, it is:
```
RtApiAlsa: callback thread error (RtApiAlsa: audio read error for device (Lenovo USB Webcam (plughw:Webcam,0)): Channel number out of range.) ... closing stream.
```

---

### Post by roadkillbunny on 2008-06-19
Any suggestions?

---

### Post by jmstanleyjr on 2008-09-18
Sorry this has been awhile by the dates, if you still need help..... 
I have a lenovo 3000 N200,just installed Ubuntu a couple of days ago had the same issue. 
Right click Volume control icon. 
select open volume control
choose file change device.
check radio button to choose each device and make sure controls are up and not muted.

Jess

---

### Post by magicfab on 2008-12-22
A bug has been opened about this:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/310760](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/310760)

---

