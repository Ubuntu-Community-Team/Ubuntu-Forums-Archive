---
title: "System sounds keep switching Onkyo TX-SR606 modes on &amp; off"
date: 2014-09-28
forum: Hardware
---

### Post by geemac2 on 2014-09-28
Hi

I have my HTPC S/PDIF output connected to the S/PDIF audio input on my Onkyo TX-SR606 Receiver.
When there is no audio from Ubuntu's system sounds the receiver sits idle, as soon as the system makes a sound such as a key click, the receiver then switches to DTS or the proper audio mode momentarily and no sound is not heard due to the switching delay. The same issue even with audio via HDMI.
This gets to be annoying when running a program that sends an alert such as Skype or GROWL, it switches the receiver but no sound is heard.  Running any other audio such as YouTube or XBMC video or audio is fine since the sound is constant and even with silences in a video it is fine since the audio data is still there.
Apparently there is some sort of a way to set the audio in a configuration file or some sort of setting.  I have seen this some time ago and can't remember what it was.  I have Auto Mute in ALSA disabled and that does not have any effect on the receiver switching modes.  Any help would be greatly appreciated.

Thanks
GEE


[COLOR=#008000][SIZE=3][FONT=century gothic]***UPDATE***[/FONT][/SIZE][/COLOR]...

I found a fix for my situation. 
Just make an easy edit to ***default.pa* **
***Sudo leafpad /etc/pulse/default.pa***

Comment this line out. ***load-module module-suspend-on-idle***  {Roughly line 127 if you have line numbers in your editor}
To look like this. ***#load-module module-suspend-on-idle***
Save your changes.  In the terminal type ***pulseaudio -k*** then enter.  The change will then automatically take effect.

---

