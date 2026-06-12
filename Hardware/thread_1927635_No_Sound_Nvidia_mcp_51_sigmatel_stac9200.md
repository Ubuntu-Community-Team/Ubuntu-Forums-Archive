---
title: "No Sound Nvidia mcp 51 sigmatel stac9200"
date: 2012-02-18
forum: Hardware
---

### Post by HurryUbu on 2012-02-18
Hey,

i Have a big problem and not really long on Ubuntu Studio 10.10.

I have a Nvidia MCP51 Sound(chip) with Sigmatel Stac 9200 on a Notebook

since 4 days i do everything that i can find on google but there is no sound. i have seen some threads where people have solved there Problem but i tried everthing i read on google and nothing has worked 4 me
if i watch a video on Youtube pavumeter shows that there is so amplitude same on listen to mp3 but no real sound not on speakers not on headphones

if you need some more informations please let me know
with code ;-) 

thx in

---

### Post by gordintoronto on 2012-02-18
In my experience, the most likely thing is that sound is muted. If you click on the speaker icon, you can select "Sound Preferences." Click on the "output" tab, there's a mute button.

(You could also tell us what appears there, the device and the connector.)

To get more options, you could install Alsamixer and run it from the Terminal. Make the terminal window big so you can see what's what.

---

### Post by Rodney9 on 2012-02-18
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)


Also you could try pavucontrol

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.

sudo apt-get install pavucontrol

Rodney

---

### Post by HurryUbu on 2012-02-27
sry 4 beeing so latley,

i tried pavucontrol, and the speakers are not muted the earjack is unmuted too. 
i can see that the amplitude is working if i watch a video on youtube or run music in vlc or any other programm but there is no sound 

this was my my:

get new Ubuntu Studio on My medion ram 2080 notebook

alsa and pulseaudio was installed and working 
modprobe.d doc was filled with options snd-hda-intel modell=auto and different other types which are listed in Stac 92xx doc

i have used both guides before i wrote the text ^
right now i have seen that the amplitude from the inputdevice is simoltanious working with the outputamplitude 

it wont work

---

