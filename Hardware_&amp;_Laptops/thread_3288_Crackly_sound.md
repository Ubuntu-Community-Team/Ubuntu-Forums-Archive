---
title: "Crackly sound"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by Burgundavia on 2004-11-04
I have been using Ubuntu for a while now and occasionally get very crackly sound. 
The important parts:
-Warty, vanilla, with ATI drivers
-Crystal CS4281 Audio

The symptoms:
-All system sounds are crackly (logon, logoff, load program)
-Muine about half the time is crackly (0.6.3)
-Totem is crackly all the time (with both gstreamer and xine backends)
-CD Player is never crackly

As this is an occasional bug, I am ripping out my hair trying to find the problem

Corey

---

### Post by tfwo on 2004-11-04
I had similar problems with alsa vs. oss: if you have alsa, try enabling oss; is you have oss, try alsa. Run gstreamer-properties to find out, what you're using for gstreamer.
Sometimes, switching to esd (ick!) can help. But this is only in the worst cases. You could try to install esd-alsa. Tweaking alsa can also help, check the alsa wiki for the asoundrc documentation.
The xine configuration for totem and muine is stored in their config directories. check xine.config for audio driver as well.

---

### Post by robert on 2004-12-05
As I posted elsewhere -

[www.ubuntuforums.org/showthread.php?t=6433&highlight=sound+kde](www.ubuntuforums.org/showthread.php?t=6433&highlight=sound+kde)

that since installing KDE the sound on my installation has become crackly/scratchy /static-like. This includes system sounds and using mplayer to play audio from file and streaming from radio stations, although playing CD's seems OK.

Going to "Volume Control" I've found that both the crackling and the audio level increases/decreases with adjustment of PCM but only the audio varies with adjustment of VIA DXS.

If anyone knows what the problem/solution is here ...

---

### Post by theantix on 2004-12-15
[QUOTE=robert]As I posted elsewhere -

[www.ubuntuforums.org/showthread.php?t=6433&highlight=sound+kde](www.ubuntuforums.org/showthread.php?t=6433&highlight=sound+kde)

that since installing KDE the sound on my installation has become crackly/scratchy /static-like. This includes system sounds and using mplayer to play audio from file and streaming from radio stations, although playing CD's seems OK.

Going to "Volume Control" I've found that both the crackling and the audio level increases/decreases with adjustment of PCM but only the audio varies with adjustment of VIA DXS.

If anyone knows what the problem/solution is here ...[/QUOTE]

Do you mean it's crackly in KDE or everywhere?  I've found that my sound was crackly by default in Ubuntu, but it was solved by changing the audio sink to alsa in the gstreamer-properties and restarting gnome -- just as the other poster in this thread recommended.  Perhaps KDE has a tool to configure the audio sink for it's sound server?  It might be worth a try to see if the OSS and ALSA sinks have the same problem.

---

### Post by adbak on 2004-12-15
I, too, have been having this problem.  I can't pinpoint any programs that cause this as I've heard the crackling sound (which, for me, only lasts a few seconds) with any number of programs open.  It occurs with or without any other video/audio playing.

[QUOTE=tfwo]I had similar problems with alsa vs. oss: if you have alsa, try enabling oss; is you have oss, try alsa. Run gstreamer-properties to find out, what you're using for gstreamer.[/QUOTE]

I ran gstreamer-properties and changed my Default Sink for audio from ESD to ALSA and tested it and heard a beep (let's see if this fixes the problem).  I then switched the default source from ESD to ALSA and clicked the Test button, but there was nothing to heard.  Any ideas or suggestions?  Is it that big of a worry that I have no sound for my souce?

---

### Post by macewan on 2004-12-20
[QUOTE=adbak]I, too, have been having this problem.  I can't pinpoint any programs that cause this as I've heard the crackling sound (which, for me, only lasts a few seconds) with any number of programs open.  It occurs with or without any other video/audio playing.



I ran gstreamer-properties and changed my Default Sink for audio from ESD to ALSA and tested it and heard a beep (let's see if this fixes the problem).  I then switched the default source from ESD to ALSA and clicked the Test button, but there was nothing to heard.  Any ideas or suggestions?  Is it that big of a worry that I have no sound for my souce?[/QUOTE]
 same here. if I grab the title bar of a window & move the window around the screen the sound would clear up. or if there was something compiling in the back ground

---

### Post by robert on 2004-12-27
[QUOTE=theantix]Do you mean it's crackly in KDE or everywhere?  I've found that my sound was crackly by default in Ubuntu, but it was solved by changing the audio sink to alsa in the gstreamer-properties and restarting gnome -- just as the other poster in this thread recommended.  Perhaps KDE has a tool to configure the audio sink for it's sound server?  It might be worth a try to see if the OSS and ALSA sinks have the same problem.[/QUOTE]

I've changed to Debian Sarge now and got this problem again - KDE isn't and hasn't been installed. Both Audio Sink and Source are set to ALSA in GStreamer Preferences. 

There's much about the quality of the sound drivers in other lists, but I could get ALSA sound working properly, at least intermittently, on Fedora Core 2 and, of course, it worked OK when I first installed Ubuntu.

Quite an enigma still.

---

### Post by plebeien on 2004-12-28
Do you have something relative to OSS ? alsa-OSS for example ? If yes, uninstall it and see if it's better. I've got a problem of that kind with XMMS and it's working fine now, I got crappy sound in Gaim but may be from ESD.

---

### Post by plebeien on 2004-12-28
ok for gaim was ESD, no more problem. hope will be ok for you.

---

### Post by robert on 2004-12-28
[QUOTE=plebeien]Do you have something relative to OSS ? alsa-OSS for example ? 

No, alsa-oss is not loaded. Do have libsdl1.2debian-oss which, I think, is something MPlayer, which I've just loaded on Sarge, needs.

However was muting everything I didn't need (as suggested on a Debian list) in 'Volume Control' using the 'Test' facility for alsasink in 'GStreamer Preferences' to generate the sound, stopped the sound and went to restart the sound when I got:

-Error-

-Failed to construct test pipeline for 'ALSA - Advanced Linux Sound
Architecture'- 

Went to play .rm and .mpg (CD's, DVD's and .wmv are usually OK) and the noise had vanished.

I still don't know quite what is at the bottom of it.

---

### Post by macewan on 2004-12-30
[QUOTE=robert][QUOTE=plebeien]Do you have something relative to OSS ? alsa-OSS for example ? 

No, alsa-oss is not loaded. Do have libsdl1.2debian-oss which, I think, is something MPlayer, which I've just loaded on Sarge, needs.

However was muting everything I didn't need (as suggested on a Debian list) in 'Volume Control' using the 'Test' facility for alsasink in 'GStreamer Preferences' to generate the sound, stopped the sound and went to restart the sound when I got:

-Error-

-Failed to construct test pipeline for 'ALSA - Advanced Linux Sound
Architecture'- 

Went to play .rm and .mpg (CD's, DVD's and .wmv are usually OK) and the noise had vanished.

I still don't know quite what is at the bottom of it.[/QUOTE]
 sudo setpci -v -s *:* latency_timer=40

^ this works for me after reading through:

[http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html)

specificly

[http://www.sabi.co.uk/Notes/linuxSoundLatency.html](http://www.sabi.co.uk/Notes/linuxSoundLatency.html)

---

### Post by robert on 2005-01-01
[QUOTE=macewan]sudo setpci -v -s *:* latency_timer=40

Adding

Option "PciRetry" "true"

to the device section of /etc/X11/XF86Config and/or /etc/X11/XF86Config-4 is often also suggested.

Not sure it was what cured mine, but haven't had it back since my last posting (muting out what was not using).

---

### Post by Xian on 2005-02-06
[QUOTE=robert]As I posted elsewhere -since installing KDE the sound on my installation has become crackly/scratchy /static-like. This includes system sounds and using mplayer to play audio from file and streaming from radio stations, although playing CD's seems OK.

Going to "Volume Control" I've found that both the crackling and the audio level increases/decreases with adjustment of PCM but only the audio varies with adjustment of VIA DXS.

If anyone knows what the problem/solution is here ...[/QUOTE]
In KDE goto the start menu > select "Run Command" > Type in "kmix" > Run
This will open a speaker icon in the system tray.

Right-click on the kmix icon and select "Configure KMix"
Tick any boxes not already selected and click apply/okay

Right-click on the kmix icon again and select "Show Mixer Window"
Tick the box that says "Advanced"
A new menu will appear below the mixer bars

Untick the box "IEC958 Input" if you have it visible.
This should be the problem, however....

If the cracking persists, continue to untick boxes until the conflicting source is located.

---

### Post by reedlaw on 2005-04-02
I have gotten the crackling all along too, most noticably while playing MP3s and movies.  Originally running ESD, I tried switching to ALSA in gstreamer but still had the problem.  Then I tried OSD under gstreamer and the crackling was reduced dramatically!  But I still could hear a trace of static and crackling.  When there is no sound there is still some hiss in my speakers that stops when the system shuts down the ALSA daemon on shutdown.
Can I run the sytem without any ALSA daemon?  How can I eliminate the remaining static?
This seems like a really confusing issue to me.  Why are there so many sound options?  What can be done to bring about a solution that really works?

---

### Post by macewan on 2005-04-02
[QUOTE=reedlaw]I have gotten the crackling all along too, most noticably while playing MP3s and movies.  Originally running ESD, I tried switching to ALSA in gstreamer but still had the problem.  Then I tried OSD under gstreamer and the crackling was reduced dramatically!  But I still could hear a trace of static and crackling.  When there is no sound there is still some hiss in my speakers that stops when the system shuts down the ALSA daemon on shutdown.
Can I run the sytem without any ALSA daemon?  How can I eliminate the remaining static?
This seems like a really confusing issue to me.  Why are there so many sound options?  What can be done to bring about a solution that really works?[/QUOTE]


sudo setpci -v -s *:* latency_timer=40

does work for me

---

### Post by skoal on 2005-04-05
[QUOTE=macewan]sudo setpci -v -s *:* latency_timer=40

does work for me[/QUOTE]

Thanks for the advice macewan.  I haven't tried this out yet, but will tonight.  I too have been experiencing crackly pops in my sound *only* after upgrading to hoary today.  Before (in warty), whether it was the sound in GDM login or even playing from VC/1, it was really smooth and clean.  Something has changed.  I'll try out your suggestion.

kernel 2.6.10-5-386
alsa-[base|utils] 1.0.8
Sound Blaster Live!

---

### Post by cymkhat on 2005-05-17
I installed fedora core 2 on my system(via 82xx chipset) and the sound was working perfectly fine. mplayer was able to play the sound neatly and cleanly without any
 crackling sounds and noise.

Then i opened the gnomemeeting (Gnome video conferencing tool) and connected with another gnomemeeting on another fedora core 2 machine (via 82xx chipset). After the call session, i closed the gnomemeeting. then i played an mp3 song using mplayer and the CRACKLING sound started. i dont know what went wrong.

I searched the entire web for around 3 days full time and tried all the possible solutions - but nothing worked out. i tried every possible workaround but in vain. Then i took another machine (same configuration ) and installed a fresh fedora core 2 on it and again the same thing happened. Then i realised that the gnomemeeting is doing some shitty thing which i dont know. so i started - closed - started - closed - started - closed this gnomemeeting application and initiated some calls / closed them and then the SOUND again was clear again - i am not sure what this gnomeeting is doing with my sound.

i am really pissed off with fedora core 2 multimedia capabilities.

just wanted to share my experience

---

### Post by wedid151 on 2007-05-15
> **macewan said:**
> same here. if I grab the title bar of a window &amp; move the window around the screen the sound would clear up. or if there was something compiling in the back ground


[Debt Consolidation skin treatment solar Equity Line Credit magnets](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

