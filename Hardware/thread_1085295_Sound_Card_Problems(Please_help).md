---
title: "Sound Card Problems(Please help)"
date: 2009-03-02
forum: Hardware
---

### Post by ExplicitViper on 2009-03-02
i have the Creative Sound Blaster Fatal1ty Series soundcard, and i can not get this stupid thing to work correctly. I WAS able to hear the startup noise and the AIM noise that you hear from the pidgin messenger, i was just unable to hear stuff from website stuff (i.e. [www.youtube.com](www.youtube.com)). Now i am unable to hear anything. in my sound options it says:

Sound Events
OSS - Open Sound System

Music and Movies
Sound Playback: Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS) (Not Connected)

Audio Conferencing
Sound Playback: Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS)(Not Connected)
Sound Capture: Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS) (Not Connected)

Default Mixer Tracks
------nothing is here-------

i followed theses threads and the problem has just gotten worse:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[https://help.ubuntu.com/community/So...ng%20alsamixer](https://help.ubuntu.com/community/So...ng%20alsamixer)
[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

also, when i go into the Terminal and type aplay -l, it says no soundcards found. BUT before i did those threads that i listed above, it was recognizing my sound card. i dont know what to do now.... i really dont want to re-install ubuntu.

---

### Post by ylla on 2009-03-05
The Exact same thing just happened to me...re-installed the drivers and they worked and had sound again.  I rebooted...and the same thing happened again, "not connected" It was working fine the past few weeks too! VERY frustrating indeed.

---

### Post by Snocrash on 2009-03-05
Same thing with my old SBLive! Value. Sound just quit working last night after an update (libcurl and network manager) and a reboot. I opened up the gnome volume controler and my SB was not even listed. I did a quick lspci and the card was listed there. So next was lsmod and all the modules were loaded. So next I check dmesg and noticed the EMU10k1 module loaded but then failed for error -5. (Have not looked that up yet). So I figured I would try a reboot just in case something glitched. As suspected there was still no sound. So I reinstalled the kernel image and modules in case something went wrong there. Still nothing. but now the card does not even show up with lspci and no modules try to load......

Could be hardware I guess, but I don't think so....

Any ideas.....

Thanks,

-Sno

---

