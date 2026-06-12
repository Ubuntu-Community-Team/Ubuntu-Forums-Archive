---
title: "how to map the usb audio devices to card number and device number"
date: 2010-10-01
forum: Hardware
---

### Post by TechHub on 2010-10-01
Hello thanks in advance,
 
Please,
 
let me know how to get the card number and device number to attaached USB device/headset???
 
i was using lsusb and arecord -l or aplay -l but those have limitation of not having generic info

---

### Post by IcarusR on 2010-10-01
On my system aplay -l gives card & device numbers...

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
[COLOR="Red"]card 0:[/COLOR] Intel [HDA Intel], [COLOR="Red"]device 0:[/COLOR] ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Red"]card 0:[/COLOR] Intel [HDA Intel], [COLOR="Red"]device 6:[/COLOR] Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Red"]card 1:[/COLOR] default [C-Media USB Headphone Set  ], [COLOR="Red"]device 0:[/COLOR] USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Is this not what you are looking for, if not be more specific.

---

### Post by TechHub on 2010-10-04
hello sir,
 
thaks for your time and help...
CN - card number and DN - device number 
 
yes i need to get the CN  and DN which you have shown in the replay but how to relate that CN and DN to attached USB devices.
 
because aplay -l only gives information of CN and DN as generic like USB Audio, aplay -l dont show USB device GUID number.
 
e.g i need informaton like
 
if GUID (USB device ID ) number of device is "046d:08c5" then what is CN and DN for this device.
 
In your case on card 1:
 
[COLOR=#ff0000]card 1:[/COLOR] default [C-Media USB Headphone Set  ], [COLOR=red]device 0:[/COLOR] USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
what is GUID or USB device ID of this device?

---

