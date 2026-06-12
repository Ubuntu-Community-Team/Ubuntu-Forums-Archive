---
title: "Having problem with USB Headset in Dell Inspiron 6400"
date: 2009-07-25
forum: Hardware
---

### Post by ovroniil on 2009-07-25
I have just installed Ubuntu 9.04 on Dell Inspiron 6400. I connected a USB headset [model HS-4075p] but Dell couldn't detect that completely. That headset has a volume controller to control the volume of laptop. That controller worked well (with that controller I can control my Laptop's speaker volume!) but the ear-phone and microphone didnot work.

How to make that work? Any suggession?

---

### Post by kostkon on 2009-07-26
Let's see if it is recognised: open a terminal and give
```
aplay -l
```
if you can see it listed then it is working fine.

The next step would be to install the *PulseAudio Device Chooser* utility. More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

If you want to make the controller control the volume levels of your headset, then you need to go to *System &#8594; Preferences &#8594; Sound* and select the *Devices* tab. Then, in the *Default Mixer Tracks* section you need to select your USB headset from the *Device* drop-down menu and below it the volume level you want the controller buttons to control; in most cases a master volume level will be available for you to select.

Hope that helps.

---

### Post by ovroniil on 2009-09-25
With that code it shows that Ubuntu recognizes the device. Then I installed the *PulseAudio Device Chooser* utility from Synaptic. But still no sound!

Here is the output of aplay -l

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

[COLOR=Red]card 2[/COLOR] is the USB headphone.

[sorry for the very late response, as the headset was not working, I lent it to one of my friends. Now he returned it and now I am still in the same situation!]

---

