---
title: "No sound after configuring ALSA on Feisty"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by Tally Solleni on 2007-11-18
Specs:
Sound card- Intel82801DBM (ICH4-M)
System- Compaq Presario M2000
OS- Ubuntu 7.04 "Feisty Fawn"
Kernel- 2.6.20-16-generic

History:

I am a newbie to the world of Ubuntu.  Recently, I installed "Feisty Fawn" on my trusty laptop.  The sound worked perfectly well until I tried to configure the sound, in order to process MIDIs and record sounds as well.  I located the correct ALSA drivers etc., but after installing them, my sound did not work at all.
When I try to open Volume Control, I receive the following message: "No volume control GStreamer plugins and/or devices found."
When I try to edit volume preferences, nothing happens.

[[IMG]http://img118.imageshack.us/img118/4268/sound001rx0.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=sound001rx0.jpg)
Opening System>Preferences>Sound works, but clicking the "Test" button causes a strange error message (see image).  Also, note that there is nothing listed under "Mixer Tracks".

I tried many tutorials, but none of them solved this issue.  Likewise, I made certain that I had all available Gstreamer plugins, along with a variety of other programs and drivers, but that also has achieved nothing.  I checked a number of forum topics which featured problems similar to mine, particularly [this one]("http://ubuntuforums.org/showthread.php?t=543793") and  [ this one]("http://ubuntuforums.org/showthread.php?t=615513"), following the advice contained therein.  However, I still have no sound.  When I try to open ALSA Mixer and all similar programs, they either do not open or crash immediately.  I am at my wits' end.

Currently, the only thing I can think of to do is to upgrade to Gutsy Gibbon and see if the situation improves.  Is this a good course of action, or will it lead to more problems?

---EDIT---
I updated to Gutsy and now I have my sound back.  The downside is that I have yet to configure it to play MIDIs, and to be honest, I'm not quite sure that I should- since that was the source of the problem to begin with.  It could mean that I'll have to part with my much-loved MIDI collection, but I don't know what else I can do.

---

### Post by mushroomcloudwarrior on 2007-11-19
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

This seemed to help me

---

