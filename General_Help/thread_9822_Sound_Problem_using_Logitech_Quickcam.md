---
title: "Sound Problem using Logitech Quickcam"
date: 2005-01-01
forum: General Help
---

### Post by amerigo5 on 2005-01-01
I have Logitech Quickcam Notebook Pro and I installed pwc-10.0.6a successfully. The problem is that when I have the Quickcam plugged into the computer (USB port), the sound doesn't work. If I unplug it, the sound works. 

The video part of the Logitech Quickcam Notebook Pro is working. It can capture images using GnomeMeeting. But the microphone doesn't work. On GnomeMeeting, when testing the Audio Devices thru Configuration Druid, nothing works - no voice and sound.

Can anyone give me some pointers on resolving the issue? Thanks in advance.

---

### Post by nemin on 2005-01-02
[QUOTE=amerigo5]I have Logitech Quickcam Notebook Pro and I installed pwc-10.0.6a successfully. The problem is that when I have the Quickcam plugged into the computer (USB port), the sound doesn't work. If I unplug it, the sound works. [/QUOTE]
Most webcams have a built-in microphone, so Ubuntu thinks it's a 'soundevice'.
Usually your problem is caused because Ubuntu uses the webcam as default sounddevice. I don't know how to fix that, but at least you have an indication now what's causing the problem :)

---

### Post by swingincelt on 2005-02-03
This process of adding the soundcard module to /etc/modules worked for me.

[http://www.ubuntuforums.org/showthread.php?p=55102](http://www.ubuntuforums.org/showthread.php?p=55102)

Cheers,
SwinginCelt

---

