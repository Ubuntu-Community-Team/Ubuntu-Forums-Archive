---
title: "My laptop speaker doesn't work"
date: 2008-11-08
forum: General Help
---

### Post by thangola on 2008-11-08
Hi all ^^.
I have a HP Compaq 6530s and I've just installed Ubuntu 8.10 on it. It seems that everything is so good. But I still have a problem with my laptop speaker. It doesn't work.
When I play music with my external speakers, there's no trouble, the sound is good. But when I unplug the audio jack, there's no sound.
Any ideas?
Thanks for read ^^.

---

### Post by thangola on 2008-11-08
Plz help me ^^.

---

### Post by thangola on 2008-11-09
Up once again.

---

### Post by thangola on 2008-11-12
Is there anyone here. I cant use laptop without the speaker >.<. Please help me.

---

### Post by patrickballeux on 2008-11-12
In a terminal, launch "alsamixer -Dhw:0".  See if you have different volumes for internal/external speakers.  Raise them all until you hear something...

On my old averatec, I have to raise the volune DX1 to have sound on internal speaker.

Good luck!

---

### Post by thangola on 2008-11-12
Thanks for reply ^^.
When I open the Alsa Mixer, there is no column above the Headphone label. And when I raise value at columns, there's any change (still no sound).

---

### Post by patrickballeux on 2008-11-12
Ok, in a terminal, run this:

> puselaudio -k

This will stop the pulseaudio sound server.  So now, you should be configure to run only Alsa...

Open your volume control, and in System - Preferences - Sound, set all your sound to you Alsa sound card (Generally, the 1st in the list).

From your volume control, play with all your volumes, also note that you have a "Prefenreces" button at the top of the Volume Control window.  Click on it and add all items in there...

Surely there is one of the volume that will manage internal speakers (Make sure that none is muted).

Good luck!

---

### Post by thangola on 2008-11-12
I've just tried the command "**pulseaudio -k**" and do as u show, but there is any change :(. My internal speaker still keep silent :(. Do u think that Ubuntu cannot recognize my speaker?

---

### Post by thangola on 2008-11-13
Is there any one here? Plz help me.

---

### Post by patrickballeux on 2008-11-13
Once stop the Pulseaudio server, you have to play with your volumes to test.


On a sound card, you have different volumes, but some times, pulseausio does not consider all of them. It's in the ALSA layer that you can play with these settings.

That's why I was asking your to stop pulseaudio (puselaudio -k), and then play with the Volume Control, or "alsamixer -Dhw:0" in a terminal) to try to find the missing volume.

Also, it can be a switch to activate (checkbox)...

---

### Post by thangola on 2008-11-13
This is screenshot of my Sound Preferences and Volume Control after I adjust:

[IMG]http://duythang.net.googlepages.com/SoundPreferences.png[/IMG]

[IMG]http://duythang.net.googlepages.com/VolumeControl.png[/IMG]

The pulseaudio was killed. And there is no sound. What should I do now?

---

### Post by patrickballeux on 2008-11-13
Now I'm stuck...

What shows up when you click on preferences? 

And what are the options/switches?

Have you look at the OSS driver (instead of HDA ALSA Mixer)?

This is a real mystery...

---

### Post by thangola on 2008-11-14
Hmm. Now I cant use my external speakers, too >"<.  I cant restart the pulseaudio.
```
~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
```
:confused::confused::confused::confused:
Plz help me start the pulseaudio again >"<.
(Ubuntu is not friendly as I think >.<).

---

### Post by patrickballeux on 2008-11-14
This generally mean that pulseaudio is still loaded...

Try this to kill pulseaudio 

```
killall -9 pulseaudio
```

Then restart it:

```
pulseaudio -D
```

And make sure that no software is running preventing the reloading of pulseaudio...


> **thangola said:**
> Hmm. Now I cant use my external speakers, too >"<.  I cant restart the pulseaudio.
```
~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
```
:confused::confused::confused::confused:
Plz help me start the pulseaudio again >"<.
(Ubuntu is not friendly as I think >.<).

---

