---
title: "Connect PC to Yamaha amplifier"
date: 2016-03-03
forum: Hardware
---

### Post by Richiegs on 2016-03-03
I want to connect my PC to a Yamaha amplifier through a USB port, but Yamaha driver only supports Windows and Apple. I would like to know if there is a Ubuntu driver for this. Thank you very much.

---

### Post by Bucky Ball on 2016-03-03
*Thread moved to **Hardware**.*

Have you tried plugging it in and seeing what happens?

Without a more detailed description of what this USB connection is supposed to do and the outcome you are trying to achieve by connecting it, we are in the dark as far as offering support.

You haven't mentioned the model of amp nor the version of Ubuntu you are using. Please provide links if you've used any to try and solve the issue and let us know anything you've tried to this point. 

Plug it in, open a terminal, and:

> lsusb

Is it there? Post the output back here between code tags (see the link in my signature).

---

### Post by Richiegs on 2016-03-04
I am using Ubuntu 14.04. I am looking for a driver, so that I can play music from my PC to amplifier to speaker. When I tried to plug in the usb cable to the amplifier - Yamaha a-s 801, nothing happened.  When I typed "lsusb" in the terminal, I got the following: 
Bus 001 Device 004: ID 055d:3021 Samsung Electro-Mechanics Co. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 072f:2200 Advanced Card Systems, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Bucky Ball on 2016-03-04
If you want to play music through your amplifier from your computer simply plug a regular audio cable into the headphone jack of the computer and the other into the input socket of the amp. Turn up the volume and you're done. 

You'll probably need an adapter for the headphone end of the cable. Not sure how you would get audio from the computer to the amp via USB. Is that even possible with this amp?

Anyway, as mentioned, just use and audio cable. Job done.

PS: Please use code tags for terminal output. See the link in my signature at the bottom of this post.

PPS: I see no Yamaha amp plugged in via USB. Was it plugged in when you ran the 'lsusb' command?

---

### Post by Richiegs on 2016-03-04
Yamaha a-s801 has a DAC and has a USB port on the back of the amplifier to connect with the PC.  By plugging a audio cable into the headphone jack of the computer and the other into the input socket of the amp, the sound quality is not that good simply because my Dell PC does not have an independent sound card.

---

### Post by Bucky Ball on 2016-03-04
And in the amp manual, what does it say that USB connection is there for? What does it do? Is it so you can play through the amp and record via USB onto computer? Is it for playback?

Have a look in the amp manual.

---

### Post by Richiegs on 2016-03-04
the USB port is for playback. It has driver for PC and Mac, but not Linux.

---

### Post by Bucky Ball on 2016-03-04
Ok. Let's get to the bottom of this. I'm just reading [the manual]("http://download.yamaha.com/api/asset/file/?language=en&site=usa.yamaha.com&asset_id=63281") myself. Do this in *_exactly_* this order.
_____

Turn off the PC and the amp. 
Plug the USB cable in. 
Turn on the PC and let it get to a desktop.
Then turn on the amp.
Turn the input selector on the front of the amp to 'USB'.
_____

Ok, now open Pulseaudio Volume Control in Ubuntu. It should be there but install if it isn't already. 
_____

Get some music playing on the computer using any app and click the 'Playback' tab in PAVControl.
You should see the audio stream happening in the 'Playback' window.
To the right at the top of that box is a drop-down menu where you can select an output device. Click it.
Turn down the volume on the amp. 

The big question: Is &#8220;Yamaha USB DAC&#8221; there for you to select? If it is, select it and slowly turn up the volume on the amp.
_____

Now give the output, between code tags, of

> lsusb

PS: One sweet looking amp.

---

### Post by Richiegs on 2016-03-04
Unbelievable.  it works without downloading a particular driver. Many thanks.
Bus 001 Device 010: ID 0499:3111 Yamaha Corp. 
Bus 001 Device 011: ID 05ac:1267 Apple, Inc. 
Bus 001 Device 004: ID 055d:3021 Samsung Electro-Mechanics Co. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 072f:2200 Advanced Card Systems, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Richiegs on 2016-03-04
I find Yamaha USB DAC in sound setting.

---

### Post by Richiegs on 2016-03-04
I wonder if I need Pulseaudio since I found Yamaha USB DAC in sound.

---

### Post by Bucky Ball on 2016-03-04
Pleased to hear it. Someone else might be able to advise with that, but If it's working, I would leave things as they are. Up to you to research further and tweak at your own risk. ;)

Please mark the thread as solved by using thread tools at top right of the page (or see the link in my signature).

PS: The sequence I gave in the previous post and given in the manual I linked to is I think the way to crack it. Make sure both off, cable in, PC on, amp on and should be set to go. And yes, a lot of things 'just work' in Ubuntu as the drivers are already in the kernel, no need to install them manually, but the amp is probably just seen as a standard USB device by Ubuntu as it probably follows the guidelines for one. 

Enjoy. :)

---

