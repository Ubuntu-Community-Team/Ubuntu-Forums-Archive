---
title: "Problems with microphone"
date: 2009-06-14
forum: Hardware
---

### Post by oohnirav on 2009-06-14
I posted this on the Linux Mint forums, but I haven't received help for a few hours, and I guess I'm a bit anxious.

I'm using the main edition of Linux Mint 7 on my HP Pavilion dv9700, and I just set my sound to work through esound instead of pulseaudio (if that matters). My internal microphone doesn't seem to be working, as I noticed recently in Skype (it also doesn't work in the recorder). Can anyone help me find a driver or solution? 

I'm still relatively new to any Linux distro, so I'm sorry if I'm not posting something else that could help find the source of the problem. If that's the case, ask me what you need to know, and I'll supply it.

I'd be grateful for any help that anyone can provide!

EDIT: I have additional information that might help...
When I go into volume control, check everything in the preferences, and click on the 'recording' tab, the microphone icon has a red x over it. However, when I click to get rid of the red x, exit the volume control, and re-enter the volume control, the red x is back. For some reason, I can't enable the microphone.

My microphone seemed to be using "conexant high definition smartaudio" according to Windows.

---

### Post by oarion7 on 2009-07-03
bump

I also have this problem. I unmute it, exit, and it's muted again. And in fact if i try to use the microphone while the switch is shown umuted, it still doesn't work.

---

### Post by oarion7 on 2009-07-03
> **oarion7 said:**
> bump

I also have this problem. I unmute it, exit, and it's muted again. And in fact if i try to use the microphone while the switch is shown umuted, it still doesn't work.

Ok so I admit I'm still a bit of a newbie particularly in regards to audio in Linux, I haven't yet figured out how all the different protocols relate to each other (esound, alsa, pulseaudio....) After doing more or less exactly what you had done (but in Ubuntu 8.10) and having the same situation, I uninstalled esound, then reinstalled and reconfigured PulseAudio as my default audio, at which point no audio was working at all, and so I then installed esound as well, and by the time I checked the recording tab in Volume Control I had several "devices" to choose from, under one of which it was stuck muted, and under another it was not, and I am now able to record audio. Not exactly sure what I did though.;)

EDIT: was able in fact to remove esound, for me for whatever reason on this new installation, esound was not working and so I had to completely switch back to pulse. so I can't provide help to answer your question other than the rather elementary suggestion you double check the device under Volume Control. good luck

---

