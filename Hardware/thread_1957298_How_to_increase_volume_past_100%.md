---
title: "How to increase volume past 100%"
date: 2012-04-12
forum: Hardware
---

### Post by markmaus on 2012-04-12
I have just switched from Ubuntu to Lubuntu on an Asus EeePC 1000H Netbook.  It is much faster, but the volume is way too low.  I have the volume levels cranked up to 100% on all of the controls that I can find.  In Ubuntu I could right click on the volume icon and go into settings and boost the volume past 100%.  Is there some way to boost the volume in Lubuntu?
Thanks

---

### Post by markmaus on 2012-04-22
Any ideas?  Anyone?

---

### Post by marinara on 2012-04-22
my mom's notbook has a volume control in an On screen display.  try that,
then use alsamixer, which you should run from lxterminal.

if get need help with alsamixer, let me know, i've been looking for a decent manual for it

---

### Post by Rodney9 on 2012-04-22
```
sudo apt-get install pavucontrol
```

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.



These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

---

### Post by Yellow Pasque on 2012-04-22
Lubuntu does not use pulseaudio, so there is no volume control that goes past 100%.

---

### Post by markmaus on 2012-04-23
Rodney9 thanks, your advice has solved my problem.  "sudo apt-get install pavucontrol" was all it took.  Now I have a program called PulseAudio Volume Control under the Sound and Video menu.  I can now increase the volume to 153%!

---

