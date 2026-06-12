---
title: "Sound won't come out of functioning USB speakers"
date: 2008-08-28
forum: Hardware
---

### Post by Morphenius on 2008-08-28
I just set up my fiance's old Gateway laptop (previously running Windows XP) to use Ubuntu.  Just about everything works except for an oddity with sound.  When I plug in her USB speakers, the speakers emit sound and respond perfectly well to sound tests, but all sound still comes out of the laptop's built-in speakers.  It seems like the OS knows about the USB speakers and knows how to use them but just hasn't been told to do so.

Any suggestions?

Thanks in advance for any help!

---

### Post by fauzie on 2008-08-28
Under System -> Preferences -> Sound, do the Test buttons work?

---

### Post by Morphenius on 2008-08-28
> **fauzie said:**
> Under System -> Preferences -> Sound, do the Test buttons work?

Yes.  When it's on "Autodetect," the test buttons generate sound from the laptop's speakers.  When I use the drop-down menu to select "USB Audio" instead, the test buttons pump sound out the USB speakers as one would expect.

However, setting them all to "USB Audio" seems to have no effect.  For instance, YouTube videos still insist on playing the audio through the laptop speakers, and .mp3 files also play on the laptop's built-in speakers.

---

### Post by Crafty Kisses on 2008-08-28
Post the results of this command > lsusb

---

### Post by Morphenius on 2008-08-28
> **Codename said:**
> Post the results of this command > lsusb

Bus 003 Device 004: ID 04e8:6734 Samsung Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0d8c:0001 C-Media Electronics, Inc. 
Bus 002 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 0000:0000

When doing this, I have four devices plugged in: a USB optical mouse, a USB keyboard, the speakers, and a cell phone (Jukebox, plugged in to add some songs - that's the Samsung).

---

### Post by markbuntu on 2008-08-28
If you are using pulseaudio, you can change the default stream output in the Pulse Audio Volume Control

pavucontrol

You may have to get it with Synaptic or apt get if you can't find it in Applications/Sound and Video. It is very handy if you have more than one device and need to change between them. You can set you usb speakers to default by right clicking on them in the output section and change playing streams to it by right clicking on them and choosing move stream.

Also, you should change the defaults in System/Preferences/Sound to ALSA instead of autodetect. If you really want to get into this, you can read my guide:
 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

