---
title: "Microphone not working"
date: 2010-12-02
forum: Hardware
---

### Post by gfajdi on 2010-12-02
Hello,

I have a problem in Ubuntu 10.10 in that the microphone attached to my headphones just doesn't work. The microphone works perfect in Windows 7, which means that this is not a hardware issue.

Just to compare Windows 7 with Ubuntu:
Creative's Windows driver seems to able to automatically
manage volume controls. It displays (unmutes?) only those
controls in which a device is attached. For comparison with Linux
controls below, here are available Windows controls:

&#65279;Playback:
Speakers (set to default)
Digital Audio Interface (disabled)

Recording:
Microphone (set to default)
Line-in (disabled)
Auxiliary (disabled)
S/PDIF in (disabled)

By disabled I mean greyed-out.

Here are Audacity device information logs for Windows 7 and Ubuntu
if that helps:

[http://www.mediafire.com/download.php?3hjo5l3zbz9kehx](http://www.mediafire.com/download.php?3hjo5l3zbz9kehx)

I have the 2.1 speaker system and the headphones attached to the
green Front speakers output at the same time via an audio
Y-splitter, which in my case isn't a cable, just a connector with
two holes and one male jack to plug it into the green hole.

The mike from the headphones is plugged into the blue Mic/Line in
hole. See here:

[http://pdfguides.com/creative-labs-sound-blaster-audigy-se-features-specifications.html](http://pdfguides.com/creative-labs-sound-blaster-audigy-se-features-specifications.html)

 Let me also give you a complete rundown of all the
available controls in Linux:

Output controls (Playback):

Master (100/100)

All S/PDIF controls muted or volume set to 0/0
Analog Center/LFE: muted
Analog Front: 100/100
Analog Rear: muted
Analog Side: muted
CAPTURE Feedback: 0/0

Thorough testing I found out that the CAPTURE control causes screeching in speakers if it is set to volume above 60. CAPTURE cannot be muted.
Here is the recording of the noise:

[http://www.mediafire.com/?5j4z8ono0qx9y8d](http://www.mediafire.com/?5j4z8ono0qx9y8d)

Input controls (Capture):

Line in: 0/0
Mic: 100/100
Phone: 0/0
Aux: 0/0

Then there are three more controls, which do not have a VU meter
at all. I can only toggle them between respective values. These
controls and their possible values are:

1. Analog source:
a) Mic
b) Line in
c) Aux
d) Phone

Currently set to Mic

2. Digital Source:
a) IEC958 out
b) i2s mixer out
c) IEC 958 in
d) i2s in
e) AC97 in
f) SRC out

Currently set to AC97 in

3. Shared Mic/Line in
a) Line in
b) Mic in

Currently set to Mic in.

Neither of the input controls can be muted and with the last
three controls one the values must be set (i.e. it is not
possible to set them to NONE).

Can anyone help?

Thanks.

---

### Post by lidex on 2010-12-02
What do you currently have selected for 'Profile' on the 'Hardware' tab in 'Sound Preferences'?

---

### Post by gfajdi on 2010-12-03
Analog Stereo Duplex. I also tried Analog Stereo Input but the Audacity meter remains motionless.

---

### Post by gfajdi on 2010-12-11
I _finally_ managed to get my microphone to work.

I set CAPTURE feedback to 81/81
Analog Source to Mic
Digital Source to i2s in
Mic/Line in to Mic

Works like a charm.

---

### Post by Skopuningurin on 2011-01-13
HOw did you make work?
I think I got the same problem :'(
Damn annoying

---

### Post by lidex on 2011-01-13
> **Skopuningurin said:**
> HOw did you make work?
I think I got the same problem :'(
Damn annoying
Use your mixer to set the values he provided above.
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by Skopuningurin on 2011-01-14
> **gfajdi said:**
> I _finally_ managed to get my microphone to work.

I set CAPTURE feedback to 81/81
Analog Source to Mic
Digital Source to i2s in
Mic/Line in to Mic

Works like a charm.

Ok.. I set teh capture feedback to 81/81.. But that's it.
I have no idea how to set " Analog Source to Mic " and so is with the rest.

---

