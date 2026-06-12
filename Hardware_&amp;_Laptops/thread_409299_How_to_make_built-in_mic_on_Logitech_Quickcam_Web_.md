---
title: "How to make built-in mic on Logitech Quickcam Web work?"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by joheri on 2007-04-14
This is the output from the lsusb command:
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 001 Device 001: ID 0000:0000  

When I run Kopete the camera works just fine, but there is no option as to adjust/try the built-in microphone. I have also tried to record a sound in Sound Recorder and it doesn't work.

Any ideas on how to activate the built-in microphone?

(I currently run Ubuntu 7.04)

EJ

---

### Post by Spartan.II.117 on 2007-04-16
I beleve that you have to blacklist the audio module so that the usb audio module will take priority.

---

### Post by joheri on 2007-04-17
I am a real newbie on Linux. Are you able to describe how to do that?

EJ

---

### Post by Spartan.II.117 on 2007-04-17
to blacklist audio:
in a terminal window, type:
sudo gedit /etc/hotplug/blacklist

add a line that says "audio" 

i'm something ol a linux noob myself, but i had just seen this answer not 10 munites before i saw your post. so let me know if it works!

---

### Post by nicksukharev on 2007-04-17
> **joheri said:**
> This is the output from the lsusb command:
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 001 Device 001: ID 0000:0000  

When I run Kopete the camera works just fine, but there is no option as to adjust/try the built-in microphone. I have also tried to record a sound in Sound Recorder and it doesn't work.


I have a builtin camera+mic in my laptop from Logitech and while I had to look for camera drivers the microphone was working from the very first install of Dapper. I am running Gnome and I can see the microphone as yet another device in the volume control with the name USB Device 0x046d:0x08c6 (Alsa mixer). Right now I have it configured in skype only (it has separate settings for input and output cards). I was able to configure alsa to use the USB mic as default input device and speakers as default output via alsa configuration file (.asoundrc). Check if volume manager can see your mic first and if it can, you should be able to play with this configuration file to fine-tune your system. I do not know any way to set the default capture device via GUI.

here is my device info:
Bus 005 Device 004: ID 046d:08c6 Logitech, Inc.

---

### Post by joheri on 2007-04-17
Spartan, your suggestion did not work since there is no such file as blacklist. There also isn't any directories by that name (hotplug).

---

### Post by Spartan.II.117 on 2007-04-17
sorry, figured it was worth a shot.

---

