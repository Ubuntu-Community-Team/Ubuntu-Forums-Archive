---
title: "Macbook 7,1 audio issues"
date: 2010-11-02
forum: Hardware
---

### Post by theSuperman on 2010-11-02
I followed the guide located [here]("https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Sound"). I know that was written for a MacBookPro, and I only have a Macbook, but everything seems to be working properly, except for some audio issues. I have the "Analog Stereo Duplex" profile selected in "Sound Preferences."  When I click the "Test Speakers" button, the right speaker sounds like it has much more bass than the left. I played around with alsamixer, but none of the settings there seem to be able to fix this. I am probably using an incorrect setting, since I used the macbookpro guide. But there is no 7,1 guide for Macbook that I could find anywhere. 

Has anyone had the same kind of issue?

---

### Post by lidex on 2010-11-03
> **theSuperman said:**
> I followed the guide located [here]("https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Sound"). I know that was written for a MacBookPro, and I only have a Macbook, but everything seems to be working properly, except for some audio issues. I have the "Analog Stereo Duplex" profile selected in "Sound Preferences."  When I click the "Test Speakers" button, the right speaker sounds like it has much more bass than the left. I played around with alsamixer, but none of the settings there seem to be able to fix this. I am probably using an incorrect setting, since I used the macbookpro guide. But there is no 7,1 guide for Macbook that I could find anywhere. 

Has anyone had the same kind of issue?

There is a forum for apple users:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Beyond that you may wish to try this.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=imac24 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Or try this model:
```
mbp3
```

---

### Post by theSuperman on 2010-11-03
I had already tried the mbp3 model, and the imac24 model did not work either. So far, the only model that has worked has been the mbp55.  Are there actually more than 2 speakers built into the macbook? If so, it almost seems as if the left speaker is being treated as a rear speaker, not having as much power.

---

