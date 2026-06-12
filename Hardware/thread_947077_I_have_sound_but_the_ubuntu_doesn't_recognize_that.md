---
title: "I have sound but the ubuntu doesn't recognize that I have a sound card"
date: 2008-10-13
forum: Hardware
---

### Post by jaredc91 on 2008-10-13
I have a weird problem, or at least I think its weird but I'm new to linux so I could be wrong. 
Like the title says I can hear sound fine and all of that works from the system sounds, ie the startup and shutdown sounds, to youtube videos and mp3s, but there is a x over the volume icon and when I click on it it says "No volume control GStreamer plugins and/or devices found." 
I cannot adjust the volume due to the sound card not being recognized so it is at about 50 percent I would say.
I just need to know if anyone can help figure out why my audio card is not recognized but I can hear everything normally.

I did the steps from the link below to try to get everything working as I have an Acer Aspire 6920
[http://ubuntuforums.org/showthread.php?t=921637](http://ubuntuforums.org/showthread.php?t=921637)

Any help would be greatly appreciated.

Tim

---

### Post by jaredc91 on 2008-10-14
No one has any ideas?

---

### Post by atarisan on 2008-10-14
i facing the same problem, really frustrating, especially from a newly migrant from WinXP :(

everytimes i try toplay some music files, all i got is just an error message "Failed to connect stream: Invalid argument" or
"output audio unavailable" 

but when I run the hardware testing, everything seems to be fine.... bummer.

btw, I'm using Sony Vaio PCG-V505AC

---

### Post by patrickballeux on 2008-10-14
Hi,

This is strange I have to admit, but let's try to see what we can do.

We'll try to setup your pulseaudio correctly to make sure that it will work as expected.

Let's start:

Open "System - Preferences - Sound" : Make sure that everything is set to Pulseaudio...

If you don't see "Pulseaudio", then we have to install/reinstall puseaudio...  (But for now, I'll assume that you have it installed correctly...)

As another steps, from a terminal, launch:

```
> gstreamer-properties
```

In the audio tab, make sure that capture and playback are set to pulseaudio.

Ok, this is for the basic setup...

Now open a terminal and install these packages (or you can install these package from Synaptic also...):

```
> sudo apt-get install gstreamer0.10-pulseaudio padevchooser pavucontrol pavumeter paprefs paman libasound2-plugins libsdl1.2debian-pulseaudio

```

These will give you the tools to inspect your pulseaudio server to make sure that it is working.

At this stage, to make sure that everything is in place, reboot the computer...  Once rebooted, and logged in, you should see a new icon in your notification area "Pulseaudio applet" (Looks like a jack connection of earphones).

You can open this, and everything should work (I hope)...

I think that your soundcard is locked by an application and prevent pulseaudio to grab the ressource.  Sadly, in Ubuntu 8.04, the implementation of pulseaudio is a little shaky (It is new in this release) you some steps are required sometimes to make sure that everything is in place.  Hopefully, next release will fix this issue...

Now on your turn to tell me the results...

Good luck!

---

### Post by CJay554 on 2009-01-14
I have updated an option for making the sound work on an aspire 6920 by updating your ALSA drivers to 1.18, go back to my guide and try again!

[http://ubuntuforums.org/showthread.php?t=921637](http://ubuntuforums.org/showthread.php?t=921637)

---

