---
title: "No HDMI audio at 1080p at 60Hz on an ASUS Chromebox on 16.04, 17.04."
date: 2017-05-13
forum: Hardware
---

### Post by mpb_ on 2017-05-13
I have an ASUS Chromebox ("Panther" version), Celeron CPU, 2GB RAM, integrated Intel graphics, running Ubuntu 16.04 amd64, connected to a 1080p Samsung HDTV. At 1080p/60Hz, sound over HDMI almost never works, and when sound over HDMI does work, it works only briefly and then goes silent. Ubuntu does not appear to detect the failure of sound. The HDMI audio device always appears in Pulseaudio, and you can see the volume meter going up and down in pavucontrol even though no sound is produced.

If I decrease the resolution to 720p, or 768p, sound works. If I decrease to 1080i, sound works. If I decrease the refresh rate to 30Hz at 1080p, sound works. If I go back to 1080p at 60Hz, sound stops. It is as if a bandwidth limit is being exceeded, and the computer is silently discarding the HDMI audio data to reduce bandwidth. Changing the resolution or refresh rate does not appear to cause any relevant entries in /var/log/syslog.

I have tried both the 4.4 and 4.8 kernels on 16.04. I get the same problem with Ubuntu 17.04 with a 4.10 kernel.

I installed LibreELEC on the same Chromebox. At 1080p/60Hz on LibreELEC, the sound usually works. When the sound does not work, changing the refresh rate to 30Hz and then back to 60Hz reliably causes the sound to start working at 60Hz. LibreELEC is running on a 4.09 kernel. My Acer Aspire One laptop running 16.04, when connected to the HDTV, does 1080p/60Hz with sound without problems.

I suspect that LibreELEC is configuring the graphics driver differently from Ubuntu. Or perhaps the LibreELEC kernel is compiled differently. I suspect ChromeOS would also work successfully at 1080p/60Hz, but I am not willing to go through the hassle of reverting the BIOS and reinstalling ChromeOS just to check. (After all LibreELEC works.) Unfortunately, I only have one HDMI TV/monitor with built in speakers, so I cannot test with other displays.

I have not tried Debian, but I probably could try Debian. I could also try Ubuntu 14.04.

Possibly related threads:
[https://ubuntuforums.org/showthread.php?t=2335294&highlight=hdmi+audio+1080p](https://ubuntuforums.org/showthread.php?t=2335294&highlight=hdmi+audio+1080p)
[https://ubuntuforums.org/showthread.php?t=2341578&highlight=hdmi+audio+1080p](https://ubuntuforums.org/showthread.php?t=2341578&highlight=hdmi+audio+1080p)
[https://ubuntuforums.org/showthread.php?t=2257189&highlight=hdmi+audio+1080p](https://ubuntuforums.org/showthread.php?t=2257189&highlight=hdmi+audio+1080p)
[https://ubuntuforums.org/showthread.php?t=2227187&highlight=hdmi+audio+1080p](https://ubuntuforums.org/showthread.php?t=2227187&highlight=hdmi+audio+1080p)

I would be interested in any suggestions anyone has for analyzing, diagnosing, or solving the problem.

I would be interested in any theories about what might be causing the loss of HDMI audio at 1080p/60Hz.

I would be interested in any theories about what specifically LibreELEC might be doing differently.

Here is some information from a Live session of 17.04.

```

ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 17.04 \n \l

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

ubuntu@ubuntu:~$ dmesg | egrep -i 'snd|sound|audio|hdmi'
[   26.051564] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   26.150036] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC283: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
[   26.150040] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   26.150041] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   26.150043] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[   26.150044] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[   26.150046] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[   26.153120] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input5
[   26.153263] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
[   26.153376] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[   26.231555] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
[   26.231714] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9

```

---

### Post by mpb_ on 2017-05-13
I just did another experiment, which yielded a very surprising result.

I booted a Live session of 16.10.  I opened sound settings and did the "Front Left" and "Front Right" sound tests.  I have to play two test sounds close together.  I will not hear the first sound, but I will hear the second one (and any later sounds).  If I play no sound for about 10 seconds, then I will not hear the first sound I play after those 10 seconds.

If I press the "Test" button (to play the "Front Left" sound test, for example), and then if I start playing music in Rhythmbox before the "Front Left" test sound finishes playing, then Rhythmbox will play sound.  If I stop Rhythmbox, and then start it again, there will be no sound.  I will have to again "bootstrap" sound playback with the "Front Left" test sound.

So... this makes it seem like some sounds (small sounds?) can successfully start sound playback, but that other (longer?) sounds cannot.  Very strange.

If I get Rhythmbox playing, then turn the TV off, then back on, sound continues to play.

If I get Rhythmbox playing, then turn the TV off, the unplug the HDMI cord, then plug it back in, then turn the TV on, sound continues to play.

In a Live session of 17.04, Rhythmbox on its own will not play.  If I bootstrap Rhythmbox playback with a test sound (as described above with 16.10), I will get a couple seconds of Rhythmbox music, and then the sound from Rhythmbox will go silent, although it will visually appear that playback is continuing.  So 17.04 is worse than 16.10.

In a Live session of 16.04.2, sometimes (rarely) I can bootstrap Rhythmbox into playing music, but far more often bootstrapping yields only 1-2 seconds of playback before Rhythmbox goes silent.

---

### Post by mpb_ on 2017-05-13
Manjaro Linux 17.0.1 with a 4.9.20 kernel has the same problem.

---

### Post by mpb_ on 2017-05-13
Sound works fine with:
devuan_jessie_1.0.0-RC2_amd64-live.iso
debian-live-8.8.0-amd64-gnome-desktop.iso

---

### Post by mpb_ on 2017-05-14
I installed 14.04.4.  Kernel is linux-generic-lts-wily (version 4.2.0-27 after install).  Sound works.

If I install linux-generic-lts-xenial (that is kernel 4.4.0-75) and reboot, sound stops working.

So... somewhere between 4.2.0-27 and 4.4.0-75, something changes in the kernel (or in the way Ubuntu boots the kernel) that causes HDMI sound to stop working at 1080p on this particular hardware.  (On 4.4.0-75, I still can bootstrap the sound playback as described above.)

Given that the same problem appears in lots of other distros, I'd suspect the change is in the kernel itself.  It is interesting that LibreELEC is unaffected.

A possible (but slightly dirty) workaround might be to (backwards) install the 4.2.0-27 kernel on an install of 16.04.

---

### Post by mpb_ on 2017-06-13
Yesterday, for reasons not related to this thread, I reverted my Chromebox to ChromeOS.  No audio at 1080p in ChromeOS.  Audio works when I switch to 720p.  So the problem is now present in ChromeOS.

I don't remember this problem when I bought the ChromeBox in 2015, but I only used ChromeOS briefly then, so it could have been there.

---

### Post by dswann on 2017-06-30
I've just updated from Debian Jessie (kernel 3.16.0-4-amd64 I think) to Stretch (4.9.0-3-amd64), and have hit the issue you're seeing :(

Except for me, it seems to be a bit worse... at 1080p there's no audio, at 720p it kinda works, but very frequently cuts out for 1-5 seconds at time (i.e. unusable). At 480p, it works fine.

I've not been able to find a hint of an error logged anywhere either. I've checked syslog, messages, and the output from pulseaudio.

---

### Post by mpb_ on 2017-07-04
So this is very interesting.  Yesterday I switched my Chromebox to Developer Mode.  I used Mr. Chromebox's Kodi EZ-Setup script to install dual booting with Chrome OS and Ubuntu 16.04 (with kernel 4.4.0-83-generic).

[https://mrchromebox.tech/#kodi](https://mrchromebox.tech/#kodi)

In Chrome OS, there is still no audio at 1080p.  However, in Ubuntu, Firefox can play audio at 1080p 60Hz (for example, playing a Youtube video).  If I start audio playing in Firefox, leave that audio playing, and then start audio in a second program (such as Chrome), then that second program can continue playing audio even after I quit Firefox.

I read somewhere (I cannot remember where) that the problem might have to do with the playback sample rate.  Audio is typically played at 44,100 or 48,000 samples per second.  It could be that one rate works and the other does not.  If the sound device (the HDMI audio channel) is opened at 44,100 and then a second program tries to simultaneously connect at 48,000, then PulseAudio (or ALSA) may convert the 48,000 to 44,100 on the fly (because the output channel itself can only be at one rate at a time).  This could also explain why sound works in LibreElec.  LibreElec could be converting all audio on the fly to a particular rate.

Sample rates do not explain why sound worked 4.2 kernels, but stopped working in 4.4.

On another topic, it turns out that Chrome OS is running a 3.8.11 kernel, and fails to play sound at 1080p.  This refutes my theory that the problem was introduced between the 4.2 and 4.4 kernels.  (I guess the problem could be in Xorg, and not in the kernel.  I don't see any Xorg process running on Chrome OS.  Chrome itself may be driving the display.)

@dswann - I have never experienced problems at 720p.  Are you able to test with multiple displays/HDTVs?  I have only tested with my single old-ish 40-inch Samsung HDTV.

---

### Post by dswann on 2017-07-06
At the moment, I've not done a lot of testing - in particular, I've only tried outputting to a (cheap LED 480p) projector, with a Samsung box extracting the the Audio; this setup did work prior to upgrading though.
One thing I forgot to mention is that I'm trying to use 5.1 audio - when I drop to stereo, it works fine all the way up to 1080p. Which I guess still points to a bandwidth issue somewhere.

---

### Post by mpb_ on 2017-07-06
@dswann:  I'm confused.  If you have only outputted to a 480p projector, how do you know it works (in stereo) at 1080p?  Also, I thought you said audio worked at 480p?  So if 480p is your target output resolution, and it works, then it would seem that this problem does not meaningfully affect you.

Another point I read somewhere, is that Audio over HDMI can have different encodings.  PCM was one encoding, there may have been others.  I forget if there is a menu in pavucontrol, or somewhere else in Ubuntu's audio settings that lets you specify which enconding(s) to use.  I'm not sure if the encoding could make a difference.  The whole HDMI output channel is sort of like a black box: there does not seem to be a good way to see what data is actually being sent.  (Unless you have an HDMI capture device, which I do not.  And even with a capture device it could be a real pain to try to diagnose the captured data given the shear quantity of data that you would capture.)

---

### Post by dswann on 2017-07-07
The projector accepts 1080p, 720p & 480p (and a few other resoloutions), but it's my understanding it's only about 480p native. I say about, becasue it seems to have a native aspect ratio of 16:9, rather than 4:3 that I think 480p would normally have.


So this results in black bars down the either side of screen 480p, which aren't there at 720p or 1080p, which is why I've always used 720p up to now.
Also, it's eaiser to use with stuff like youtube in a browser window at 720p than 480p, becasue everything is awkwardly large at 480p (not a big deal, I know).

I'll see if I can find the encoding options and play with that.

---

