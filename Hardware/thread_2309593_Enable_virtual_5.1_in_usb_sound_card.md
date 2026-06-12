---
title: "Enable virtual 5.1 in usb sound card?"
date: 2016-01-11
forum: Hardware
---

### Post by Evil Wayz on 2016-01-11
Got this little usb sound card card for Xmas, package simply says "Lead 3D Sound 5.1 TIDE".

Aplay - l outputs: ```
card 1: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

The package indicates in WIndoze this sound card supports 3d positional  sound as well as virtual 5.1, as well as something called speaker shifter.  Obviously I'm not running Windows, so I'm wondering if there is a way to enable these features in Ubuntu, or is this part of the windows drivers package.  I am running 14.04, with gnome flashback and the latest Pusleaudio with eq support from the webupd8 ppa.

---

### Post by Evil Wayz on 2016-01-12
This thread referenced using pavucontrol to change settings from 2.0 to 7.1 audio, but it mentioned no method other than using pavucontrol.  I have this installed and found no way to configure the usb other than choosing digital or analog output. [http://ubuntuforums.org/showthread.php?t=1952050]("http://ubuntuforums.org/showthread.php?t=1952050")

---

### Post by Evil Wayz on 2016-01-12
Looking thru /etc/pulse/daemon.conf
I changed the default-samples from 2 to 6 ( 5.1) but I don't know how to properly denote the channel map.  bleow is what it currently says, and is commented out. 


default-channel-map = front-left,front-right

---

