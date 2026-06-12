---
title: "sound problems"
date: 2010-04-14
forum: Hardware
---

### Post by shadowcrunch on 2010-04-14
I'm having sound problems. I've read quite a few threads on different ways to fix the problems, but nothing I try works. I was running a dual-boot with Vista, with Realtek sound on my motherboard. I could play music and watch videos with full sound, but could not get sound to work in any games. I followed a site for checking and fixing sound step by step, and found out ubuntu had no support for my Realtek audio, so I disabled it. 

A few threads mentioned sound blaster had full support, so I put in my Audigy, and it worked great, for about 5 minutes before it had a kind of static distortion and stopped until I rebooted. After a reboot I had full sound, and could listen to about 2 minutes of a song before it happened again. A buddy said maybe I screwed up something in the installation, so I formatted and am now just running ubuntu. Same sound problems, but now I can listen to 2 or 3 songs before the static distortion failure. 

I can play ubuntu system sound effects fine, and the diagnostic tests all work ok. Seems to only happen when I have sound playing for more than a few seconds. Is there some particular codec or driver I might need? Can anybody please point me in the right direction? Thanks ahead of time!

---

### Post by lidex on 2010-04-15
Can you provide some info please? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by shadowcrunch on 2010-04-15
Okay, got the link here: [http://www.alsa-project.org/db/?f=488d5e7258224369c5977abb853c231d6acf823a](http://www.alsa-project.org/db/?f=488d5e7258224369c5977abb853c231d6acf823a)

---

### Post by Yellow Pasque on 2010-04-15
> I could play music and watch videos with full sound, but could not get sound to work in any games. I followed a site for checking and fixing sound step by step, and found out ubuntu had no support for my Realtek audio, so I disabled it.
How did you draw the conclusion that Ubuntu/Linux does not support Realtek chips, especially if you had it working for some apps? (Linux does support Realtek chips)

Most likely, you just needed to install libsdl1.2debian-pulseaudio because Ubuntu installs SDL's ALSA backend by default (which doesn't work well) [https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/203158](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/203158)

---

### Post by shadowcrunch on 2010-04-15
Based on what I read by the link you provided, this sounds like it will be the fix I'm looking for. I will try it in a little while and let you know. Just so I'm fully aware, should I be trying this with the Realtek or the sound blaster?

As for the Realtek thing, I had googled "ubuntu sound problems" and found [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I followed it step by step, and there's a section about a third of the page down where they have you check if alsa is using the right module, and you cross reference what your system has with a list of your driver version at [http://git.alsa-project.org/?p=alsa-kmirror.git](http://git.alsa-project.org/?p=alsa-kmirror.git)

My particular page was [http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bfcbbf88c44dd7da7c9a0fc161308d173a7d1a36;hb=ac7eedc68016f6272e5d6606924e7f09fc5c729c](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bfcbbf88c44dd7da7c9a0fc161308d173a7d1a36;hb=ac7eedc68016f6272e5d6606924e7f09fc5c729c)  and the first link tells you to scroll down until you find your sound module, and check to see if the printed output is the same. It also stated if your card was not listed, alsa won't support it yet. Instead of scrolling, since mine was listed as Realtek I did a search and it wasn't listed on the page, so according to the info provided the realtek wasn't supported with the driver version I'm running. I've only been running ubuntu since the beginning of the year, so I didn't know any better. Thanks again, and I will let you know soon!

---

### Post by Yellow Pasque on 2010-04-15
It doesn't matter whether you have the audigy in when you build ALSA. In fact, you probably want to use the audigy if possible (better audio quality if it works correctly).

> since mine was listed as Realtek I did a search and it wasn't listed on the page, so according to the info provided the realtek wasn't supported with the driver version I'm running.
The driver for HD codecs is snd-hda-intel.

---

### Post by shadowcrunch on 2010-04-15
Okay, followed the link and read about installing pulseaudio to fix sound issues, but didn't see any "how-tos" so I googled it and found [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I should add that I checked synaptic package manager and it showed pulse as being installed already. So anyway, I followed the above site step by step, and I actually have sound in games now, can watch a youtube vid without a lockup, and banshee gets through full songs unless something else tries playing audio! However, the audio still chops with static, especially in games. When the sound works, it's much better quality than it was with the realtek (that's why I bought the SB in the first place!).

So, I did everything that site mentioned, but am not even sure if everything installed properly, and don't know where or what to check to make sure. I realize people with no clue should go back to windows, but I'm trying to learn here.

---

### Post by lidex on 2010-04-15
> **shadowcrunch said:**
> Okay, followed the link and read about installing pulseaudio to fix sound issues, but didn't see any "how-tos" so I googled it and found [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I should add that I checked synaptic package manager and it showed pulse as being installed already. So anyway, I followed the above site step by step, and I actually have sound in games now, can watch a youtube vid without a lockup, and banshee gets through full songs unless something else tries playing audio! However, the audio still chops with static, especially in games. When the sound works, it's much better quality than it was with the realtek (that's why I bought the SB in the first place!).

So, I did everything that site mentioned, but am not even sure if everything installed properly, and don't know where or what to check to make sure. I realize people with no clue should go back to windows, but I'm trying to learn here.

Did you install
```
libsdl1.2debian-pulseaudio
```

---

### Post by shadowcrunch on 2010-04-15
Yes, libsdl1.2debian-pulseaudio is installed, though I'm not sure how to test if any of it is working right except just running things with sound. Games that had no sound before now have decent sound with occasional chop, and don't lock up when I close them. Linux Multimedia Studio only works when I set it for pulseaudio, but it has audio lag of several milliseconds. Banshee and Rythymbox both start to play music, but both get around a minute through a song, static to silence...the whole app screen goes gray, and if I click anything (like applications or system or whatever) it takes well over a minute for anything to happen, almost like the locked app is eating all the processing power I have.

---

