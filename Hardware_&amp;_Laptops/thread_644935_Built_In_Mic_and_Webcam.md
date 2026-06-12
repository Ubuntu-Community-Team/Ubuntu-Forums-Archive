---
title: "Built In Mic and Webcam"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by mcw00t on 2007-12-19
Right, I have a custom built laptop running Ubuntu 7.10 Gutsy Gibbon. It has a built in webcam and mic. Now, I don't know about the webcam, it might just be a simple case of downloading the right software to get it to work, but for the mic, I get an error saying that my audio capture settings aren't configured properly, and to change them in 'Multimedia Settings' - which I cannot find, any ideas?

Thanks In Advance

---

### Post by linuxwizard on 2007-12-19
For your mic look over these

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

You could try EasyCam
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by mcw00t on 2007-12-19
Right, the mic FAQ's I already checked, and the capture is unmuted and all the way up, and the mic is unmuted and all the way up, and the boost is all the way up. When I try to start sound capture, I'm greeted by an error message saying my capture settings are invalid.

When I go to 'sound' to test pipelines, I get a continuous popping from my speakers when testing the Sound Capture and an error saying unable to construct pipeline.

I've got Camorama for my webcam now, and that has an error saying that it cannot find the device.

---

### Post by linuxwizard on 2007-12-19
Could be a sound card issue. What sound card are you using ? Did you install a driver for your webcam and which one ? What make and model of your webcam ?

---

### Post by mcw00t on 2007-12-19
Not for the webcam, but I have full ALSA drivers for my sound card. It's the seemingly dreaded Intel HDA (most recent one, can't remember model number). I have normal audio working fine, after much alsa-base editing & driver installing.

I'm not too bothered about the webcam, I'll have a look at that later on, it's mainly the mic I'm bothered about.

---

### Post by linuxwizard on 2007-12-19
Look through this see if anything may help 

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by mcw00t on 2007-12-19
Sorry, I've been through all of that already when trying to get the audio working.

[http://ubuntuforums.org/showthread.php?t=643193](http://ubuntuforums.org/showthread.php?t=643193)

Is the thread, I went through and did everything suggested there.

---

