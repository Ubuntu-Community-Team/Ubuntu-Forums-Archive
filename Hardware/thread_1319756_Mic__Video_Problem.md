---
title: "Mic / Video Problem"
date: 2009-11-08
forum: Hardware
---

### Post by ragad3 on 2009-11-08
Hi,

I am using a Lenovo Ideapad U330 Notebook with Ubuntu 9.10 installed.

The audio output works great, speakers are fine, but I am having problem recording sound and using my webcam.

The Sound Recorder tool that comes with Ubuntu picks up nothing. And the video displayed on the Skype Webcam settings is blank. I don't know what to do for the video (it says it is using the /dev/video0 device).

For the MIC, I opened Sound Preferences, and found 5 tabs beneath the volume control bar. The first tab, Sound Effects, is of no relevance. In the second tab, Hardware, found that there were two devices:

_Internal Audio:_
Profile Options: Off, Analog Stereo Input, Digital Stereo Duplex ( IEC958 ), Digital Stereo ( IEC958 ) Output + Analog Stereo Input, Analog Stereo Output, and finally, Analog Stereo Duplex.
Notes: I can get my speakers working only with the last two profile options (Analog), and my mic does not work in either setting.

_RV620 Audio Device [Raedon HD 34xx Series]_
Profile Options: Off, Digital Stereo (HDMI) Output

In the third tab, Input, there was only one Input Device selected (Internal Audio Analog Stereo), and the corresponding Input Volume is at a healthy "unamplified" level.

In the fourth tab, Output, I could choose either the Internal Audio Analog Stereo or the RV620 Audio Device [Radeon HD 34xx Series] Digital Stereo (HDMI). Only with the first choice, I can use both speakers and headphones. With the second choice, I cannot use headphones.

The final tab, Applications, just displays the current applications that are playing or recording sound.

I would be immensely grateful for help in configuring my mic and webcam for use in Skype! Thank you very much. My Skype version is 2.1.0.47

- Raga.

---

### Post by Ryan B on 2009-12-03
Check out my post on:

[http://ubuntuforums.org/showthread.php?t=1002234&highlight=u330](http://ubuntuforums.org/showthread.php?t=1002234&highlight=u330)

This is how I got my camera and mic working on ubuntu 9.04. (I have subsequently broken my sound trying to get the switchable graphics to work).

(not sure how to link to a post)
R

---

### Post by ragad3 on 2009-12-05
I tried it, but did not work.

First, I tried to install uvcvideo as suggested in the other linked post, but it bailed out with a lot of compile errors. I tried to find solutions online, but there does not seem to be any.

For the audio, I guess 9.10 has redesigned the interface, and so I could not follow the instructions in your previous thread.

Please help!

---

### Post by Ryan B on 2010-01-08
Yep, the audio instruction don't work on 9.10... hmm. I haven't had a chance to play about with the webcam though this link suggests that we might be out of luck:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
Look for u330. It seems that us u330 guys might be very unlucky with the webcam. Most of the other lenovo versions seem to work fine with the new drivers.

---

### Post by hadronicchaos on 2010-01-10
I just installed 9.10 on a Lenovo U330. To check the webcam, I installed guvcview from synaptic. No problems there, the webcam seems to work fine.

However, I'm still searching for a resolution to the mic issue. Instructions from [http://ubuntuforums.org/showthread.php?t=1002234](http://ubuntuforums.org/showthread.php?t=1002234) worked on Ubuntu 9.04, but as it was pointed out, those instructions don't apply here.

---

### Post by hadronicchaos on 2010-02-07
The fix is in! I can only guess that one of the recent patches has fixed the problem in 9.10.

I raised the volume on the mic in alsamixer. Then, from the 'Sound preferences' dialog from the gnome volume control, I adjusted the amplification on the mic to reasonable levels. Testing in Skype shows that both webcam and audio are working. Unfortunately, I don't know what changed under the hood to resolve the issue.

---

### Post by Ryan B on 2010-03-12
Thanks for the update about the webcam, yep it works nicely (had to find the invert button on guvcview.

I still can't get the internal mic to work. Here is how i tried to follow your instructions. At the commandline, typed alsamixer. used arrow keys to go to Front Mic, turned that to full, then to Front Mic Boost, and turned that to full. Then I rightclicked on the speaker icon on the gnome panel and selected sound preferences. Then clicked on the input tab and turned up the amplicifaction... but when I used sound recorder I got nothing but static. On the hardware tab I have analog stereo duplex. Any help to get this last bit working. Cheers
R

---

