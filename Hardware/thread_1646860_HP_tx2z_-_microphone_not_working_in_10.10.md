---
title: "HP tx2z - microphone not working in 10.10"
date: 2010-12-16
forum: Hardware
---

### Post by robbyb413 on 2010-12-16
I'm having an issue with the integrated microphone on my tx2z laptop running Ubuntu 10.10. I'm sure this is something I've muked up or missed somehow so I created a new thread rather than cluttering up an existing general tx2z thread with this issue.

The machine dual boots Ubuntu 10.10 and Windows Vista. The microphone works flawlessly under Vista. The microphone worked when I was running Ubuntu 8.10 as well. With this fresh install of 10.10 however I cannot get it to capture sound.

Here is what I have done so far:

Installed a clean copy of Ubuntu 10.10. Updated until there were not more updates available. Installed proprietary wifi, video, and modem drivers. Ran the commands for getting touch working on the N-Trig digitizer with Vista firmware. Installed magick-rotation 1.2. 

Sound worked at that point, but could not capture in sound recorder or skype. I recalled that in Ubuntu 8.10 I needed to edit alsa-base, so I added "options snd-hda-intel model=toshiba" to the end of the "alsa-base.conf" in "/etc/modprobe.d/"

That did not change behavior, although I had more options under sound preferences for controling the mic. I used those to change the "input level" on the Mic to various levels attempting to capture sound, no luck. I tried setting the drop-down to both "Microphone 1" and "Microphone 2" without any results.

I reviewed more information, and according to [http://ubuntuforums.org/showpost.php?p=8005429&postcount=118](http://ubuntuforums.org/showpost.php?p=8005429&postcount=118) next step was to run "alsamixer", make sure "input source" was set to "front mic", and raise all the boost levels in that application. This got me to the point where Skype or Sound Recorder would capture a steady hum, but no matter how much I yelled at the mic there was no evidence that I was making an impact. No change in the levels would product a change in the results.

I found [http://ubuntuforums.org/showthread.php?t=1592115](http://ubuntuforums.org/showthread.php?t=1592115) that suggested "options snd-hda-intel model=3stack" worked for some people, so I commented out the "toshiba" line I added previously and tested "3stack". After reboot, this interestingly enough produced a result similar to istalling Ubuntu 8.10 *without* adding "options snd-hda-intel model=3stack" where sound would clip and stop functioning. Obviously that was a no go, so I reverted to "toshiba".

That same thread also suggested installing "pavucontrol", selecting the "input" tab, and lowering the volume on the right channel to zero and leaving the left channel at 100%. I tried that, no luck. I tried setting the drop-down in that app to Microphone 1 and Microphone 2 to be sure, as well as trying both Mic 1 and Mic 2 setting with the opposite setting of left channel at zero and the right channel at 100%. No matter what, I still got the same effect.

I searched some more, and found that on this machine with Ubuntu 9.04 some people had success using "options snd-hda-intel mode=acer-dmic" so I tested that. I removed pavucontrol and repeted all the steps I'd tried above - first playing with sound prefrences, then playing with alsamixer, then installing pavucontrol and playign with that. The best I could do at any stange was get a constant hum with Sound Recorder or Skype with no amount of noise made by myself at any level of volume or distance from the mic producing a recorded effect. 

I should note as well that after any change - modifying alsa-base.conf, installing pavucontrol, etc, I rebooted them machine.

At this point I've gone back to the beginning to try to start over... pavucontrol uninstalled, input is set to 100% in the sound prefrences, alsaconf is set to front mic with the levels at 100%, and alsa-base.conf's last line ends with "toshiba". I can capture no sound at all like this, not even a hum. Clicking record on Sound Recorder does nothing, as if there isn't even a Mic attached to the machine, and when I stop and hit play it errors and says stream contains no data. 

So that's where I'm at... looking for some help as to what I might have overlooked or what I can do to toubleshoot this further. Anyone have any advice? Thanks in advance.

---

### Post by robbyb413 on 2010-12-23
Bumping this, have been playing with it but still having the same issue. Does anyone have any additional trouble shooting steps or thoughts about what I might have skipped/done wrong here?

---

### Post by robbyb413 on 2011-01-02
Bumping this again, still looking for help. I'm not knowledgeable enough to fix this alone, any help is appreciated.

---

### Post by Swirlsky on 2011-01-09
i have the same problem

---

### Post by Ayuthia on 2011-01-11
Can one of you go into alsamixer and let us know which card and chip is being used?  The information is in the upper left hand corner.

Mine is showing:
```

Card: HDA NVidia
Chip: Conexant CX20549 (Venice)

```

I am currently using Kubuntu 10.10 and mine seems to be working after using pavucontrol.  I have a tx2-1025dx but they should be similar.

---

### Post by robbyb413 on 2011-01-11
Sure can... I'm showing:

Card: HDA ATI SB
Chip: Realtek ALC268

---

### Post by Ayuthia on 2011-01-11
> **robbyb413 said:**
> Sure can... I'm showing:

Card: HDA ATI SB
Chip: Realtek ALC268

Good.  It is the same (my previous results came from Natty) on mine in 10.10.

My settings are currently using the default that came with 10.10 (i.e. it is not using toshiba or 3-stack).  The only thing that I had to do was go into pavucontrol->Input Devices and click on the mute button.  From there I had to adjust the volume levels in alsamixer so that my voice was not distorted.

I think that those are the only differences that I have.  I tested mine with qarecord.

---

### Post by robbyb413 on 2011-01-11
Hrrm... so I commented out the modifications I had made to alsa-base, to match the default that came with 10.01. Rebooted the machine.

Installed pavucontrol. Rebooted the machine. To be safe.

Checked alsamixer - front mic is all the way up. (screen shot attached - alsamixer.png)

Went into gnome-sound-recorder, clicked the record button, nothing happens. The record button never grays out. Tried to play, said "stream contains no data". 

Opened pavucontrol, clicked the input tab, hit the icon to unlink the sliders, slid the "Front Right" all the way as far as it would go (to "silence"). (screen shot attached - pavucontrol.gif). Opened gnome-sound-recorder, tried to record, same result (record won't gray out, "stream contains no data" when I hit play - screen shot attached, error.gif)

Opened pavucontrol again, raised Front Right, lowered front left. Same result as above. 

So, no joy. Did I miss a step in your process? I'm confused by the part where you said you clicked on the mute button... can you elaborate? When I click the mute icon in Input Devices (Internal Audio Analog Stereo, "all except monitors" in the "show" drop down) get the same result as the above.

---

### Post by Ayuthia on 2011-01-11
> **robbyb413 said:**
> Hrrm... so I commented out the modifications I had made to alsa-base, to match the default that came with 10.01. Rebooted the machine.

Installed pavucontrol. Rebooted the machine. To be safe.

Checked alsamixer - front mic is all the way up. (screen shot attached - alsamixer.png)

Went into gnome-sound-recorder, clicked the record button, nothing happens. The record button never grays out. Tried to play, said "stream contains no data". 

Opened pavucontrol, clicked the input tab, hit the icon to unlink the sliders, slid the "Front Right" all the way as far as it would go (to "silence"). (screen shot attached - pavucontrol.gif). Opened gnome-sound-recorder, tried to record, same result (record won't gray out, "stream contains no data" when I hit play - screen shot attached, error.gif)

Opened pavucontrol again, raised Front Right, lowered front left. Same result as above. 

So, no joy. Did I miss a step in your process? I'm confused by the part where you said you clicked on the mute button... can you elaborate? When I click the mute icon in Input Devices (Internal Audio Analog Stereo, "all except monitors" in the "show" drop down) get the same result as the above.

It does not look like you missed a step.  The mute button works like you described however mine was muted for some reason.  The only other thing that I can see from your pavucontrol picture is that you don't have an volume feedback bar showing in the Input Devices tab.  Can you try and change your Show: to have All Input Devices?  You should get two items to show (Monitor of Internal Audio Analog Stereo and Inter Audio Analog Stereo).  You should then get a sound feedback indicator.  Mine is currently bouncing around because of the fan and my typing but I am guessing that yours is not.

The other thing to try out is to run gnome sound recorder from the Terminal and see if any error messages appear in the Terminal.  Another thing to try is to install qarecord and run it from the Terminal.  You will need to click the capture button.  If you do that, the Terminal might show an error message.  Mine is doing that in 11.04 because ALSA could not grab the device.

---

### Post by robbyb413 on 2011-01-12
Tried messing with pavucontrol after setting show to have all input devices. Screen shots attached, as you can see once I do that gnome-sound-recorder will show it as recording, but no matter what configuration I have the sliders set to there is nothing showing in either level meter. Playback of the file is silence. I tested my audio to make sure it was actually replicating sound, and mp3s and such play just fine.

Screen shots of pavucontrol showing some other funny behavior as well... when gnome-sound-recorder is running pavucontrol shows it there but says no applications currently recording?

I ran gnome-sound-recorder from the terminal and got:

(gnome-sound-recorder:2748): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed

I then ran qarecord from the terminal and got:

Error opening PCM device plughw:0 (Device or resource busy)
Could not open PCM for capture.
ALSA capture failed!

I tried g-s-r and qarecord as myself, with sudo, and with gksudo and it didn't seem to care either way - all gave the same error. Tested qarecord with pavucontrol open and experimenting with the sliders with the same error each time I clicked capture.

If the information matters, in pavucontrol these are the other settings:
Playback - system sounds slider to 100%
Output Devices - set to Analog Speakers, both sliders to 100%
COnfigurations - internal audio profile is set to Analog Stereo Duplex.

---

### Post by Ayuthia on 2011-01-12
I'm stumped.  I had the same error message as you for qarecord and after I rebooted, it started working again.  So I am not for sure what is causing that.

I did find this [link]("http://ubuntuforums.org/showthread.php?t=1071180").  There was another link at the end of the thread that showed how to configure it for the NVidia version which should be similar to ours.

If you have the 10.10 liveCD, you might check and see if it works in there.

---

### Post by windozh8ter on 2011-03-14
A user named, lidex, solved my microphone problems with the following thread:

[http://ubuntuforums.org/showthread.php?t=1680221](http://ubuntuforums.org/showthread.php?t=1680221)

Specifically, post #6 in that thread seemed to do the trick for me. After following all of his suggestions, my alsamixer showed a blank for my internal microphone. Arrowing over to it, then up arrow to increase the level clinched the deal for me.

---

### Post by robbyb413 on 2011-05-19
It's been a while since I had time to look at this issue, but I used some of post 6 in that last link and it seems to have gotten the mic working to an acceptable level in sound recorder. Still some buzz in the background, but I left sound recorder on while I was standing 5 or 6 feet away having a phone conversation and it picked it up pretty clearly. Thanks for that suggestion.

It's still not working in Skype unfortunately, just records dead air. I'm guessing that's my fault somewhere, going to play with those settings. Not sure if I should mark this as solved or not based on that.

---

### Post by robbyb413 on 2011-05-19
Worked it out with Skype. Got it working - not sure why but when I loaded skype 2.2 and then opened volume control through the new button in the control panel it reset my settings. Pulled levels back up and tweaked some stuff and now it's working. Marking this as solved. Thanks. :thumbup:

---

