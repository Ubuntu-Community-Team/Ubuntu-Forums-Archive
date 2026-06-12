---
title: "Mic input disappeared on 11.04 Dell E6510"
date: 2011-06-27
forum: Hardware
---

### Post by vincegata on 2011-06-27
Hi,

The mic input all of a sudden disappeared on my laptop after one of the updates. So I do not have mic anymore on recorder or Skype. My laptop is Dell E6510. Here is the output of aplay -l:

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


How can I restore the mic?

Thanks!

---

### Post by vincegata on 2011-06-28
I've tried editing /etc/modprobe.d/alsa-base.conf file with whatever settings I could find on Internet but nothing is helping. 

It looks like the driver is gone. The "Sound Preferences->Input->Choose a device for sound input:" text box is just empty. Please see attachment. (Mute is not the problem.)

Any tips would be appreciated!

---

### Post by vincegata on 2011-07-06
please

---

### Post by lidex on 2011-07-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by vincegata on 2011-07-06
Here we go:


[http://www.alsa-project.org/db/?f=471d24b713a150ee63ebcd049af0934443ecde99](http://www.alsa-project.org/db/?f=471d24b713a150ee63ebcd049af0934443ecde99)

---

### Post by lidex on 2011-07-06
change your alsa-base.conf edit from this:
```
options snd-hda-intel model=ref
```
to this:
```
options snd-hda-intel model=s14
```
**Reboot**
Now make sure you have a duplex profile selected in sound preferences.

---

### Post by vincegata on 2011-07-07
It worked!

Thank you so much for helping!!!

---

