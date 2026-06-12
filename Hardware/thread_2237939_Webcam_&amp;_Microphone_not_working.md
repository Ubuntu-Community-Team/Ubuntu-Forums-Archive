---
title: "Webcam &amp; Microphone not working"
date: 2014-08-04
forum: Hardware
---

### Post by Tristan_Williams on 2014-08-04
I have a Logitech c120 webcam.

It works when I run "cheese" but in skype, it's not recognized.

What can I do to get it recognized by skype?

Another problem is that the webcam has a builtin microphone.
Shouldn't I be able to use the mic as just a mic? or does it only work when I am recording with the webcam?

Edit:
It might help to add that the webcam is /dev/video0

---

### Post by gordintoronto on 2014-08-05
What version of Ubuntu? What version of Skype?

In Skype, I select Options, then Video Devices, and my webcam automatically shows up under "Select webcam". It's /dev/video0, just like yours.

Yes, you should be able to select the microphone any time. The way to select it depends on what version of Ubuntu you are using. For some reason, many microphones have a default state of Muted.

---

### Post by Tristan_Williams on 2014-08-06
I am using Xubuntu 14.04
Skype version 4.3.0.37

---

### Post by mastablasta on 2014-08-06
I remember having similar issue (but with another cam). what solved it was a preload command. you can try (copy and paste into terminal):
```

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

if it works just add this line into your Skype shortcut.

edit - one more thing - I am not sure if this lib is already installed. if it's not use software center or synaptic to install it: *libv4l-0*

---

### Post by Tristan_Williams on 2014-08-06
That fixed the webcam in skype part.

How can I use the mic from the webcam to record audio?

---

### Post by Vladlenin5000 on 2014-08-06
You need to select the audio input - a new USB device - in the sound settings.

---

### Post by Tristan_Williams on 2014-08-06
> **Vladlenin5000 said:**
> You need to select the audio input - a new USB device - in the sound settings.

What? I don't understand what you mean

---

### Post by mastablasta on 2014-08-07
I am not sure where and how the sound settings look like in Ubuntu but in Kubuntu you would go into system settings -> multimedia where oyu would change the input for your chip and just set it to camera. In my case the camera mic get's recognised there and I can select it. you should see your camera in the mic input.

I still haven't figured out which of the mics available it is in Audacity (there is so many of inputs one needs to select the correct one there), so I couldn't try recording with it yet :)

---

### Post by Tristan_Williams on 2014-08-07
I'm running Xubuntu and there is no sound related menu in the settings manager. I can go to PulseAudio volume control but /dev/video0 isn't a device in there

---

### Post by mastablasta on 2014-08-08
uf I would need to check this at home where I have xfce in vbox.

What about alsamixer? a CLI tool. does it show the mic volume?

---

### Post by Vladlenin5000 on 2014-08-08
[http://ubuntuforums.org/showthread.php?t=1941411](http://ubuntuforums.org/showthread.php?t=1941411)

---

### Post by Tristan_Williams on 2014-08-08
No it doesn't show up in alsamixer. And definitely not pavocontrol (the default volume control in Xfce)

The mic on the camera doesn't work in Skype either. The only place it works is Cheese

---

