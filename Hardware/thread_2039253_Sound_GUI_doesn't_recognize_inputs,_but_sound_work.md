---
title: "Sound GUI doesn't recognize inputs, but sound works"
date: 2012-08-08
forum: Hardware
---

### Post by azile19 on 2012-08-08
This problem appeared after an update a few months ago, but I'm just getting around to working on it now.

My sound works, however the sound settings GUI does not recognize any of my inputs (speakers and a USB mic/camera).  The issue is that right now I can't use my mic/camera for skyping since the computer doesn't recognize it.  I'm not even sure where to start looking for help on this since the sound is still working, so I'm guessing it just has to do with the settings menu.

---

### Post by testblageneric on 2012-08-08
Hello,

well you can use the Pulseaudio Volumecontrol to change settings. Just run 'pavucontrol' or install it if it's not there. (I'm assuming pulseaudio is up and running.)

Regards,
Andreas

---

### Post by azile19 on 2012-08-08
When I run pavucontrol I get the following error message:



Fatal Error: Unable to connect to PulseAudio: OK

---

### Post by testblageneric on 2012-08-08
That's what man-pages are for...
Just run > pulseaudio --start as user to start the soundserver.

---

### Post by azile19 on 2012-08-08
Ok, pavucontrol is up and running, but it also doesn't see any of my devices.

---

### Post by testblageneric on 2012-08-08
Okay, you can try to run

> sudo alsactl init

to initialize your sound-devices. (and restart)

Normally pavucontrol should at least show you the input-devices, so you can try a test record with your microphone. Your webcam can be tested with guvcview or cheese. 

I'm not sure about skype, maybe you need 32-bit alsa-libs, or just change the sound settings there. (Disable 'let skype control volume levels')


 Are your sure it's not a hardware failure? you can try if a *buntu live cd detects your devices properly.

---

### Post by azile19 on 2012-08-08
I tried to initialize the sound devices, but no change.

I booted to an Ubuntu USB, and everything works.  I can see all the hardware, so I don't think it's a hardware issue.

Also, I apologize, I misspoke earlier.  I was trying to use gchat, which is where I was having all the problems.  Although the sound menu still doesn't see any devices, skype is working fine.  gchat, however, seems to have a working camera now (it didn't before), although I can't get the mic working.

---

