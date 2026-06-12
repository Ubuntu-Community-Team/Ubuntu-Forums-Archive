---
title: "Ubuntu 16.10 on Asus Zenbook 3 UX390"
date: 2016-10-20
forum: Hardware
---

### Post by galdrapiu2 on 2016-10-20
Hi there ...

Does anybody else use Ubuntu 16.10 on Asus Zenbook UX390UA?

Most of the things are working fine out of the box - as far as I can say.

But I have still some unsolved issues:
* Volume Level for internal audio is not alternable (Mute works. Volume for headphones, hdmi out and volumes for single applications is alternable))
* Fingerprint Reader (Elantech) : Fingerprint GUI "No Device Found!" ([http://home.ullrich-online.cc/fingerprint/Forum/topic.php?TopicId=572&Posts=1](http://home.ullrich-online.cc/fingerprint/Forum/topic.php?TopicId=572&Posts=1))
* Menu and Windows flickering  on HDMI-over-USB3-Video-Out (XORG Displayserver / Modsetting Driver?)


Can anybody help?

Thx Galdrapiu

---

### Post by Ossoleil on 2016-11-02
I just received my Asus Zenbook UX390UA and installed Ubuntu on it.
I am having the same issues beside the flickering. Where do you notice that?

---

### Post by rosholm on 2016-11-07
I got my Asus Zenbook 3 UX390UA yesterday.
Which guide did you follow to install Ubuntu (and are you dual booting)?

---

### Post by Bucky Ball on 2016-11-07
@galdrapiu2: Welcome. To improve your chances of support I suggest you edit your first post to one support issue and edit the thread title to reflect what that problem is.

Put the other two problems in the appropriate forums in their own threads with descriptive titles. We encourage one user, one issue per thread here. 

As for sound, what are you using to tweak it, what have you done to experiment to fix it? Have you got Pulseaudio Volume Control installed? If not, install it. Get some music playing with PAVControl open. In the 'Playback' tab, can you see the audio stream bouncing up and down near the slider? 

Go to the 'Output' tab. See the stream there? Above the stream you will see 'Port' with a drop-down menu. Start selecting devices from there or select the right device to output if you know it. Matter of experimenting because you've given no idea of your setup. Would certainly help if you did.

As for the other two, no idea, sorry. As I say, try new thread for them. Good luck. :)

---

### Post by Ossoleil on 2016-11-09
Also, I had a problem with the USB-c to DisplayPort causing tracebacks in the i915 module. I had to add i915.enable_psr=0 to the kernel boot parameters to make the tracebacks go away and be able to plug-in a DisplayPort screen reliably.

---

### Post by valllllll2000 on 2016-11-25
Anybody found a solution for the sound control issue? Just installed ubuntu 16.10 on my new ux390. Could not find any solution except for this thread.

---

### Post by Bucky Ball on 2016-11-25
> **valllllll2000 said:**
> Anybody found a solution for the sound control issue? Just installed ubuntu 16.10 on my new ux390. Could not find any solution except for this thread.

What you see is what you get. If anyone had a solution they would have posted it. You will have more luck starting your own thread specifically for the sound issue and specifically with your details. The OP here is looking for help with other things, not just specifically that, and they haven't been here for a month.

Good luck.

---

### Post by chovy2 on 2016-12-04
Can someone with a laptop output the results for `xinput list` and also the `xinput prop-list <id>` command on the trackpad?

I'm curious what all the options are, thinking about getting one of these.

Debating between these two:

Asus Zenbook UX390UA
Asus Zenbook UX330/UX330UA

---

### Post by galdrapiu2 on 2016-12-09
> **chovy2 said:**
> Can someone with a laptop output the results for `xinput list` and also the `xinput prop-list <id>` command on the trackpad?

```
>xinput list
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN1301:00 04F3:3035 Touchpad              id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Asus Wireless Radio Control                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; USB2.0 VGA UVC WebCam                       id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

>xinput list-props 12
Device 'ELAN1301:00 04F3:3035 Touchpad':
    Device Enabled (140):    1
    Coordinate Transformation Matrix (142):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    1
    Device Accel Constant Deceleration (268):    2.500000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    12.500000
    Synaptics Edges (271):    128, 3080, 98, 1731
    Synaptics Finger (272):    25, 30, 0
    Synaptics Tap Time (273):    180
    Synaptics Tap Move (274):    162
    Synaptics Tap Durations (275):    180, 100, 100
    Synaptics ClickPad (276):    1
    Synaptics Middle Button Timeout (277):    0
    Synaptics Two-Finger Pressure (278):    282
    Synaptics Two-Finger Width (279):    7
    Synaptics Scrolling Distance (280):    -73, -73
    Synaptics Edge Scrolling (281):    0, 0, 0
    Synaptics Two-Finger Scrolling (282):    1, 1
    Synaptics Move Speed (283):    1.000000, 1.750000, 0.054171, 0.000000
    Synaptics Off (284):    2
    Synaptics Locked Drags (285):    0
    Synaptics Locked Drags Timeout (286):    5000
    Synaptics Tap Action (287):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (288):    1, 3, 0
    Synaptics Circular Scrolling (289):    0
    Synaptics Circular Scrolling Distance (290):    0.100000
    Synaptics Circular Scrolling Trigger (291):    0
    Synaptics Circular Pad (292):    0
    Synaptics Palm Detection (293):    0
    Synaptics Palm Dimensions (294):    10, 200
    Synaptics Coasting Speed (295):    20.000000, 50.000000
    Synaptics Pressure Motion (296):    30, 160
    Synaptics Pressure Motion Factor (297):    1.000000, 1.000000
    Synaptics Resolution Detect (298):    1
    Synaptics Grab Event Device (299):    0
    Synaptics Gestures (300):    1
    Synaptics Capabilities (301):    1, 0, 0, 1, 1, 0, 0
    Synaptics Pad Resolution (302):    32, 31
    Synaptics Area (303):    0, 0, 0, 0
    Synaptics Soft Button Areas (304):    1604, 0, 1499, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (305):    18, 18
    Device Product ID (262):    1267, 12341
    Device Node (263):    "/dev/input/event13"
```

---

### Post by galdrapiu2 on 2016-12-09
> **Ossoleil said:**
> 
I am having the same issues beside the flickering. Where do you notice that?

the flickering problem is gone.

---

### Post by chovy2 on 2016-12-10
```
>xinput list
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN1301:00 04F3:3035 Touchpad              id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Asus Wireless Radio Control                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; USB2.0 VGA UVC WebCam                       id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

>xinput list-props 12
Device 'ELAN1301:00 04F3:3035 Touchpad':
    Device Enabled (140):    1
    Coordinate Transformation Matrix (142):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    1
    Device Accel Constant Deceleration (268):    2.500000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    12.500000
    Synaptics Edges (271):    128, 3080, 98, 1731
    Synaptics Finger (272):    25, 30, 0
    Synaptics Tap Time (273):    180
    Synaptics Tap Move (274):    162
    Synaptics Tap Durations (275):    180, 100, 100
    Synaptics ClickPad (276):    1
    Synaptics Middle Button Timeout (277):    0
    Synaptics Two-Finger Pressure (278):    282
    Synaptics Two-Finger Width (279):    7
    Synaptics Scrolling Distance (280):    -73, -73
    Synaptics Edge Scrolling (281):    0, 0, 0
    Synaptics Two-Finger Scrolling (282):    1, 1
    Synaptics Move Speed (283):    1.000000, 1.750000, 0.054171, 0.000000
    Synaptics Off (284):    2
    Synaptics Locked Drags (285):    0
    Synaptics Locked Drags Timeout (286):    5000
    Synaptics Tap Action (287):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (288):    1, 3, 0
    Synaptics Circular Scrolling (289):    0
    Synaptics Circular Scrolling Distance (290):    0.100000
    Synaptics Circular Scrolling Trigger (291):    0
    Synaptics Circular Pad (292):    0
    Synaptics Palm Detection (293):    0
    Synaptics Palm Dimensions (294):    10, 200
    Synaptics Coasting Speed (295):    20.000000, 50.000000
    Synaptics Pressure Motion (296):    30, 160
    Synaptics Pressure Motion Factor (297):    1.000000, 1.000000
    Synaptics Resolution Detect (298):    1
    Synaptics Grab Event Device (299):    0
    Synaptics Gestures (300):    1
    Synaptics Capabilities (301):    1, 0, 0, 1, 1, 0, 0
    Synaptics Pad Resolution (302):    32, 31
    Synaptics Area (303):    0, 0, 0, 0
    Synaptics Soft Button Areas (304):    1604, 0, 1499, 0, 0, 0, 0, 0
    Synaptics Noise Cancellation (305):    18, 18
    Device Product ID (262):    1267, 12341
    Device Node (263):    "/dev/input/event13"
```


Thanks I see you have the ELAN. I've heard some ship with a worse trackpad, where did you buy this one?

Have you had any issues with the trackpad?

Also do the speakers work ok? I tried my friend's with ubuntu live cd and the audio was not good. Crackling everywhere.

---

### Post by hanni_ali on 2016-12-11
To resolve the sound issue do the following:

```

sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

Change:


```

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

To this:
```

[Element Master]
switch = mute
volume = ignore


[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right


[Element LFE]
switch = mute
volume = ignore
```

This ensure the sound behaves.

I'll report back once I have the fingerprint reader working, but the sound was the only thing that was irritating me so I thought I'd share.

Hanni

---

### Post by chovy2 on 2016-12-13
This might help anyone having speaker issues:

[https://www.reddit.com/r/ASUS/comments/5grm4v/speakers_dont_work_properly_on_asus_ux390ua_on/db3ip5w/?context=3](https://www.reddit.com/r/ASUS/comments/5grm4v/speakers_dont_work_properly_on_asus_ux390ua_on/db3ip5w/?context=3)

> 
[FONT=verdana]Hello there,[/FONT][COLOR=#222222]What you experienced is a relatively common problem, fixed by installing pulseaudio-daily (google for it and the first result is the PPA, add it and install the package).
By default, a live CD will not have the latest kernel + pulseaudio package(s), needed to support the subwoofer and channel mapping for the SKU. Recent kernels + pulseaudio stacks fix that.


[/COLOR]



---

### Post by hansischmolke on 2016-12-14
@hanni_ali 
This works perfectly on my system. Zenbook 3 UX390U
Thanks a lot.

---

### Post by chovy2 on 2016-12-17
> **hanni_ali said:**
> To resolve the sound issue do the following:

```

sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

Change:


```

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

To this:
```

[Element Master]
switch = mute
volume = ignore


[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right


[Element LFE]
switch = mute
volume = ignore
```

This ensure the sound behaves.

I'll report back once I have the fingerprint reader working, but the sound was the only thing that was irritating me so I thought I'd share.

Hanni

I'm still getting scratchy audio. Did not seem to make any difference for me.

---

### Post by galdrapiu2 on 2017-01-04
> **chovy2 said:**
> Thanks I see you have the ELAN. I've heard some ship with a worse trackpad, where did you buy this one?

Switzerland

> **chovy2 said:**
> Have you had any issues with the trackpad?

NO

> **chovy2 said:**
> Also do the speakers work ok? I tried my friend's with ubuntu live cd and the audio was not good. Crackling everywhere.

Yes, audio works fine so far. With loud sound there is some vibrating of the laptop chassis.

---

### Post by galdrapiu2 on 2017-01-04
@hanni_ali

Your Code solved the audio-volume issue for me. And the Speakers sounds now more full. Thanks a lot Hanni!!!!

Galdrapiu

---

### Post by vielster on 2017-02-06
This seems to fix the sound control issues, but I have no volume output from my headphone jack...anyone have similar issue or a suggested fix?

Thanks.

---

### Post by Bucky Ball on 2017-02-06
> **vielster said:**
> This seems to fix the sound control issues, but I have no volume output from my headphone jack...anyone have similar issue or a suggested fix?

Thanks.

Welcome. Better to start a new thread with a descriptive title and more detail about your issue than jump on this on which was started by another person about their issues. Good luck. :)

---

### Post by agenthumble on 2017-03-20
I had the same problem until I opened up alsamixer and boosted the master to max. Now it all works great.

---

