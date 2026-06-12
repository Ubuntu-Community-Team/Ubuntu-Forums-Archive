---
title: "Dell Mini 10 audio disappeared"
date: 2009-11-01
forum: Hardware
---

### Post by cordage on 2009-11-01
Yesterday I decided to put Karmic on my mini after working with Jaunty on my desktop for months. Using the UNR, I got it installed and found a tutorial on fixing the graphics and wireless. Later, I found that I can view youTube video but not hear them. Video I transfered via network are the same.

I found from ubuntumini.com that it was pulseaudio and purged it. I could hear again, all video and audio files worked. I also installed alsa and esound with no change. I missed the ability to control volume through my keyboard, but less than I missed a volume control. gstreamer0.10-plugins-bad is installed in an attempt to get gnome-volume to work. My System>Preferences>Sound states it is waiting for sound system to respond.

I continued on my merry way, thinking at least I can watch South Park and Hulu online.

very recently, my audio died. I was watching trailers on apple and there was no audio. I had no audio on youTube. Restarting, I had audio for like 10 minutes before it went away. I have restarted twice now, and it has not come back.

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Silicon Image SiI1392 HDMI

I need help to get the sound card working again and (hopefully) volume controlled through UNR 9.10 Karmic Koala.

---

### Post by scout4536 on 2009-11-01
Same exact problem on my mini 10, I went back to 9.04 until this is fixed.   Everything worked fine but audio.  So now I keep looking for a fix in google.

EDIT:  Found a fix that seems to be working, my audio hasn't cut out yet:

sudo nano /etc/modprobe.d/alsa-base.conf

delete the last line: options snd-hda-intel power_save=10 power_save_controller=N

and change it to this: options snd-hda-intel model=dell

I actually think they set this file by default to turn your audio off after 10 mins????  But anyway after doing this I can even restart my machine without losing audio, before I would lose it.  Hope this helps.

---

### Post by cordage on 2009-11-02
Hi, thanks for replying

I did add the line, but it didnt change my audio. I grudgingly reinstalled pulseaudio and followed the instructions at [http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications](http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications) before restarting. I now have the audio back for both Flash and Local audio/video with my volume keys working.

I also installed the pulseaudio utilities mentioned on that page.

---

