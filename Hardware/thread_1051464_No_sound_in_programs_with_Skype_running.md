---
title: "No sound in programs with Skype running"
date: 2009-01-26
forum: Hardware
---

### Post by campbuds on 2009-01-26
I have skype set to start up during boot.

The problem is I cannot listen to music while skype is running. Whether it be a mplayer or pandora.com In fact once skype starts no other sound works until I close it.

What is the problem?

I have a Vaio vgn-cr220e if that help.

---

### Post by bettlebrox on 2009-01-26
Go to Skype's options menu, click on "Sound Devices" and configure it to use pulse for both "Sound In" and "Sound out" (if your using pulseaudion).

---

### Post by campbuds on 2009-01-27
> **bettlebrox said:**
> Go to Skype's options menu, click on "Sound Devices" and configure it to use pulse for both "Sound In" and "Sound out" (if your using pulseaudion).

I use intel

---

### Post by bettlebrox on 2009-01-27
Pulseaudio is a sound server that Ubuntu has started to use. You may be using it by default and not realise it.

---

### Post by campbuds on 2009-01-28
> **bettlebrox said:**
> Pulseaudio is a sound server that Ubuntu has started to use. You may be using it by default and not realise it.

Well, I tried it. THANKS!

My sound in skype still works and now it works everywhere else too.

---

### Post by sedawk on 2009-01-28
Audio can be locked (exclusive access).

E.g. when running mplayer to watch a tv recording I do not
get audio in avidemux (removing commercials from another tv recording).

---

### Post by kidcharles on 2009-02-16
I have the same problem of the sound in other programs not working while Skype is running. It it also the case that if other programs are making sound, Skype will not work. I don't have the option of PulseAudio in my Skype devices listing in Sound Devices. I'm running 8.04, any ideas on how to fix it?

---

### Post by tolito-cr on 2009-02-16
I have actually had a similar problem:

If my Exaile or LastFm are on, I can't make calls on skype... I have to shut them down. 

After reading several options:

-uninstall pulseaudio
-play with the audio settings on skype (all to pulse)
-reconfigure the ALSA mixer
-etc

What I have done and has seemed to work is to set all the skype settings to "pulse", except sound-in... that one I have used the default setting.

In any case I find this very odd and I hope there is a more systematic way to fix it... I have also the problem that in my sound controls the recording tab is always off, so I click thing back on (capture 1,2,3,digital, mux (whatever that is for?)) and when I get out and back it's again back to OFF... any ideas if this is related??

edu.

---

