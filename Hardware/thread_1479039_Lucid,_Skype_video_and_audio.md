---
title: "Lucid, Skype video and audio"
date: 2010-05-10
forum: Hardware
---

### Post by rbrown3rd on 2010-05-10
Running 10.04 with all updates on my new Acer 5810TZ Timeline.  I am trying to get Skype 2.1.0.81 beta to recognize the camera and microphone.  "Cheese" works fine as does "Sound Recorder" so it appears to me that Skype is the problem.  Any ideas?

---

### Post by mgcarley on 2010-05-10
I found this elsewhere just 5 minutes ago while solving the same problem:

```
sudo gedit /usr/local/bin/skype
```

add the following lines

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```

save the file, then

```
sudo chmod a+x /usr/local/bin/skype
```

Restart Skype (Applications > Internet > Skype) and video should work.

---

### Post by rbrown3rd on 2010-05-10
Did that work for you?  Didn't on my system.

Skype seems to be showing the vidcam as a choice but when I select "test" under options nothing happens.  It is detecting the camera as HD video webcam /dev/video0/ which seems correct. As I said before the camera is working and the mike is working because I can use "Cheese" and "Sound Recorder".

---

### Post by dalee on 2010-05-10
Hi,

I just messed with a similar problem myself this morning.

What I had to do to get sound working was to install puav control and then go to the input devices tab. click the middle button, in the upper right, to unlock the sliders. Then move one slider to 10 and move the other slider to 9. Click the green check mark. Then test call Skype. Evidently, pulse thinks your mic is stereo. Most laptop mics are mono. So pulse shuts the mic off.

I also thought my video wasn't working for exactly the same reason as you. It doesn't show up in the little test window. Nor does it display on my screen during a call. I just get a little blank box in the video screen. But the other person is seeing me just fine. Go figure.:confused: So I would actually try to make a call to see if it is indeed working.

dalee

---

### Post by rbrown3rd on 2010-05-10
That helps a bunch.  I assumed that because I could not see their video nor mine that it was not working at all.  The trick with the sound worked great.  When I unlocked the sliders and slid one backwards it seemed to work as an input volume control in reverse.  I made a test call and the audio was fine.  I am making a video call now but the other person is not home or answering.  I can't thank you enough for helping me with that. I hope soon to actually be able to see the other person.  That is what video calls are about isn't it?

---

### Post by richfeat on 2010-05-28
Many thanks - pavucontrol worked for me too. Acer Aspire A150 with Ubuntu 10.04 Lucid Desktop installed. The internal microphone and camera worked out of the box in Sound Recorder and Cheese, but the microphone did not work with Skype. After pavucontrol tweaking, it is working.
But how did you come by the Dark Arts (or should I say White Magic)? I guess you mean 9% and 10% by your "9" and "10"? I suppose that unlinking the stereo channels is enough to allow the mono mic to work in skype, but are the numbers trial and error, or from cool analysis? Anyway, well done!

---

### Post by rbrown3rd on 2010-05-28
Hope someone can now figure out how to get the camera display working.  Calls do work as was pointed out in this thread but I cannot see the person I am video conferencing with.  This must be peculiar to Acers because my little Aspire One 150 and my Timeline 5810 have exactly the same problem.

---

### Post by NorbertoBurciaga on 2011-02-04
I have an HP pavilion tx-1000 and I figured it out that my audio problem was due to the fact that the computer has two mics ports, one mic up in the monitor with the camera and the other one is a plugin for an external mic. The default one is the one that connects external, so to change the default mic I used **alsamixer** in a terminal, press **F4** to get to the capture screen, move cursor to <**Input Source**> and change the value from "Front mic" to "Atapi mic" with the up and down keys, then with pulseaudio volume control go and up the volume of the mic. The only problem is that I have to do this everyday :(  I need to figure it out how to make my Atapi mic be the default mic.

Since I upgrade to ubuntu 10.10 I lost my video, the person who I am calling can see me but I cannot see her, my computer has a blue led that indicates that the webcam is turned on, but also when I do the test I cannot see myself. Also cheese is working fine. So this is not a problem peculiar to Acers.

---

### Post by NorbertoBurciaga on 2011-02-04
ok video seems to be a Qt4 problem, follow this thread [http://ubuntuforums.org/showthread.php?t=1318506](http://ubuntuforums.org/showthread.php?t=1318506) 

SOLUTION: in a terminal execute skype as following:
```
export XLIB_SKIP_ARGB_VISUALS=1 && skype
```

---

