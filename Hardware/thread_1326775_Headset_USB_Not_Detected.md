---
title: "Headset USB Not Detected"
date: 2009-11-14
forum: Hardware
---

### Post by dominicx1889x on 2009-11-14
I have the Plantronics GameCom 777 ([http://www.plantronics.com/north_america/en_US/products/computer/pc-gaming-headsets/gamecom-777]("http://www.plantronics.com/north_america/en_US/products/computer/pc-gaming-headsets/gamecom-777")).
It comes with a USB dongle that is detachable. Once I plug-in the dongle to any USB port the 'On' light turns on for no more than a second and turns off. I have tried lspci and lsusb and haven't found it listed as far as I know. Nothing changes under lsusb command when unplugging and plugging in the USB. Under lspci, this appears: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03). I don't know if that might be it considering HD might be related to Dolby 5.1 digital surround sound as the dongle says. There is no hardware drivers for linux anywhere I have found. If anyone knows how to install this for my headset I would appreciate it.

--Using the jacks without the USB dongle works if I plug them in the front, but I receive poor microphone output.
--Kernel 2.6.24-25generic
--USB Adapter(Dongle) is Dolby Digital 5.1

---

### Post by RedSingularity on 2009-11-14
Have you tried adjusting the pulseaudio device chooser?

---

### Post by dominicx1889x on 2009-11-14
Well I don't believe it registers because the 'on' light turns off a second after I plug it in. So nothing is detected I think.
Edit: It works fine on Windows so I know it's not broke.

---

### Post by RedSingularity on 2009-11-14
I had a problem with mine.  I installed pulseaudio and the device chooser and that solved my headset problems.  Try this in terminal...........

sudo apt-get install pulseaudio & sudo apt-get install padevchooser

Then in sound and video click "pulseaudio device chooser"
That will start a deamon in your system try.  Go there and pick a default source and a default sink.

---

### Post by dominicx1889x on 2009-11-14
That didn't seem to work, nothing registered.

---

### Post by dominicx1889x on 2009-11-14
UPDATE:
Everytime I type 'lsusb' in the terminal I have a few weird things occur.
After entering lsusb in terminal, the usb soundcard lights up and I can hear an electrical sound in the headphones, Nothing is displayed in lsusb yet, UNTIL the light turns back off, then lsusb displays everything. I unplug it, and lsusb again and it's an instant reply but still reads out the same list. Nothing new.

---

### Post by dominicx1889x on 2009-11-14
Sorry for so many posts.
After lsusb I tried out the dmesg.
If anyone can interpret this, please explain it to me.

```
[  546.603819] usb 1-2: new full speed USB device using uhci_hcd and address 58
[  546.722655] usb 1-2: device descriptor read/64, error -71
[  546.947281] usb 1-2: device descriptor read/64, error -71
[  547.161865] usb 1-2: new full speed USB device using uhci_hcd and address 59
[  547.282676] usb 1-2: device descriptor read/64, error -71
[  547.562173] usb 1-2: device descriptor read/64, error -71
[  547.776815] usb 1-2: new full speed USB device using uhci_hcd and address 60
[  548.184068] usb 1-2: device not accepting address 60, error -71
[  548.295929] usb 1-2: new full speed USB device using uhci_hcd and address 61
[  548.707202] usb 1-2: device not accepting address 61, error -71

```

---

### Post by dominicx1889x on 2009-11-15
-bump-

---

### Post by dominicx1889x on 2009-11-15
Problem Solved:
USB Adapter is malfunctioned. Used my brother's exact same one and appears in lsusb and stays lit. Sorry for the trouble.

---

