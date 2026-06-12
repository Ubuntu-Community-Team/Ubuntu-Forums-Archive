---
title: "asus 5220 webcam issues"
date: 2010-06-14
forum: Hardware
---

### Post by bobdobbs on 2010-06-14
Hi all.

I just upgraded my laptop to lynx.

I am now wanting to set up skype. I've always had such insolvable problems with ubuntu/sound/skype that I've never bothered much with skype on linux. But I decided to give it another shot.

First of all, skype can't seem to find a video device.

I fired up gstreamer-properties. I go to video>input>test.
A dialogue comes up saying: 
"video for linus 2(v4|2): could not open device '/dev/video0' for reading and writing.

lsmod | grep vid returns:
uvcvideo               56990  0 
video                  17375  1 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
output                  1871  1 video


lsusb returns

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm afraid that I don't really know a lot about hardware or how linux handles it. 
So I would appreciate any help I can get.

Thanks.

---

### Post by bobdobbs on 2010-06-14
Problem fixed itself somehow.

I noticed that there was no sound on lappy as well.

So I followed some of the basic steps in the comprehensive sound problem guide. I uninstalled and then reinstalled alsa stuff.
After a reboot, sound was working, and webcam was fully functional.

---

