---
title: "Can't get Tascam US-122 on Intrepid to work"
date: 2009-04-16
forum: Hardware
---

### Post by jkff on 2009-04-16
Hello.

I have followed quite a bunch of several tutorials and forum posts found on Google on the topic, and it may well be the case that I've created some kind of mess.

Anyways, my current situation is as follows:

> 
jkff@jkff-laptop:/dist/drivers/audio$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0640000 irq 17
 1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 002/013)

jkff@jkff-laptop:/dist/drivers/audio$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

jkff@jkff-laptop:/dist/drivers/audio$ amixer info
Card default 'USX2Y'/'TASCAM US-X2Y (1604:8007 if 0 at 002/013)'
  Mixer name	: ''
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0

jkff@jkff-laptop:/dist/drivers/audio$ lsmod |grep usx2y
snd_usb_usx2y          32896  0 
snd_usb_lib            24192  1 snd_usb_usx2y
snd_hwdep              15236  1 snd_usb_usx2y
snd_pcm                83204  3 snd_usb_usx2y,snd_hda_intel,snd_pcm_oss
snd                    63268  17 snd_usb_usx2y,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  3 snd_usb_usx2y,snd_hda_intel,snd_pcm
usbcore               149488  8 snd_usb_usx2y,snd_usb_lib,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd

jkff@jkff-laptop:/dist/drivers/audio$ lsusb |grep Tascam
Bus 002 Device 013: ID 1604:8007 Tascam US-122 Audio/Midi Interface

jkff@jkff-laptop:/dist/drivers/audio$ dpkg -l |grep alsa-
ii  alsa-base                                  1.0.17.dfsg-2ubuntu1                                           ALSA driver configuration files
ii  alsa-firmware-loaders                      1.0.17-0ubuntu1                                                ALSA software loaders for specific hardware
ii  alsa-tools                                 1.0.17-0ubuntu1                                                Console based ALSA utilities for specific ha
ii  alsa-utils                                 1.0.17-0ubuntu3                                                ALSA utilities

jkff@jkff-laptop:/dist/drivers/audio$ cat /etc/asound.conf 
pcm.Live        { type hw; card Live; }
ctl.Live        { type hw; card Live; }

pcm.USX2Y       { type hw; card USX2Y; }
ctl.USX2Y       { type hw; card USX2Y; }

pcm.!default    pcm.USX2Y
ctl.!default    ctl.USX2Y

jkff@jkff-laptop:/dist/drivers/audio$ cat /etc/udev/rules.d/55-tascam.rules 
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"




So, the card doesn't show up in aplay -l.
That's probably the very reason I can't get amarok or xine to play sound into it: amarok tells me "xine couldn't initialize any audio drivers" when I select the alsa output plugin; xine itself simply plays everything through the built-in card however hard I try to convince it to not do so.

Attempts to follow the tutorials end up with this:

> 
jkff@jkff-laptop:/dist/drivers/audio$ sudo /sbin/fxload -D /proc/bus/usb/002/013 -s ./usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx

jkff@jkff-laptop:/dist/drivers/audio$ sudo usx2yloader
usx2yloader: no US-X2Y-compatible cards found

jkff@jkff-laptop:/dist/drivers/audio$ usx2yloader -D hw:1
usx2yloader: cannot open the index file /lib/firmware/usx2yloader/us122.conf


Changing 'ld2-ezusb.hex' to '/usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx' doesn't change things in any way.

On the card, the big red LED in the middle does shine, but others don't.

The card is surely OK because just 2 days ago I used it without problem on Windows.

My OS is Intrepid, kernel 2.6.27-11.

So, what should I do to make the card working? Or can I provide any further information?

---

### Post by jkff on 2009-04-16
Well, I resolved the issue.
For those who will probably run into it, here's the solution that worked for me:

[http://ubuntuforums.org/showpost.php?p=6127365&postcount=2](http://ubuntuforums.org/showpost.php?p=6127365&postcount=2)

I did that ln -s and immediately aplay started to list the card, and xine and amarok started to be able to play through it.

---

