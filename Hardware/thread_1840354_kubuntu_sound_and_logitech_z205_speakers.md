---
title: "kubuntu sound and logitech z205 speakers"
date: 2011-09-07
forum: Hardware
---

### Post by monkblah on 2011-09-07
Hi. I'm using kubuntu 10.04 on my laptop. Recently got a set of logitech z205 usb laptop speakers.

I plug them into the usb port. kubuntu recognizes them. In system settings/multimedia, I see the Logitech Z205 there. I can play a test sound from the z205 speakers in the system settings page.


I make it the most preferred sound device in system settings/multimedia/device preference.

When I start Dragon video player, it uses the Logitech Z205 like it should, no problem.

However, other applications that use sound, such as Clementine music player, or vlc video player, or watching youtube videos on google chrome, are still using the laptops built-in speakers, instead of the Z205.

These applications appear not to be controlled by the kde system settings program. What then, does control them?

Looking through the preferences for some of the programs, I see many options for what appear to be audio device outputs. For example, in clementine, there is a section called 'GStreamer Audio Engine', with an 'Output Plugin' menu. It has choices such as 'choose automatically', Gconf audio sink', audio sink (ALSA), Audio sink (OSS) PulseAudio Audio Sink, OSS v4 Audio sink, S/PDIF ALSA Audio sink, Sndfile sink, Audio Sink (Jack), Apple Airport Express Audio Sink. None of these seem to play through the Logitech Z205, though.

VLC has audio output options like Default, PulseAudio audio output, File audio output, UNIX OSS audio output, ALSA audio output. None of these seem to work with the Z205 either.

Not sure how Chrome sets its audio output, don't see it in the menu.

I know there are such things as ALSA, PulseAudio, OSS, /dev/dsp, xine backend,  and so on. Not totally sure how they all work together, or what software stands between my applications (eg VLC, dragon, clementine, chrome, etc) and the sound hardware.

I just want to have all the applications use the Logitech USB speakers when they're plugged in.

Anyone know about how kubuntu sound works and can help out?

---

### Post by COKEDUDE on 2012-05-29
Try this. Set your USB option to be first on the whole list. 

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/PhononKDEControlModule_001.png[/IMG]

---

