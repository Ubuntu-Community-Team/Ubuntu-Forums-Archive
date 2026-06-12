---
title: "[SOLVED] Surround Sound not working with PulseAudio"
date: 2009-01-03
forum: Hardware
---

### Post by coolaj86 on 2009-01-03
[SOLVED]

I have a SoundBlaster SBLive! Value SurroundSound capable card, but I can't get my music to play in surround.


Here's what I've done so far:

I tested and found that only the **front** speakers were working: 
```
speaker-test -Dsurround40 -c4 -l1 -twav
#speaker-test -Dsurround51 -c6 -l1 -twav # for 5.1
#speaker-test -Dsurround71 -c8 -l1 -twav # for 7.1/CODE]
Surround sound wasn't working at all so after some googling I found that I could open the **Preferences tab** in
[CODE]gnome-volume-control
```
And there are all of the hidden channels. I enabled **surround**. (5.1 users sound also enable **Center** and **LFE**)
I ran speaker-test again and this time I can hear the **rear** speakers in the test, but not when playing an mp3.

I open up **totem** and go to **Edit -> Preferences -> Audio** and enable **4 channels**.
When I play the song again, nothing has changed, it's still only on the front to speakers.

I figure maybe it has to do with the fact that mp3s aren't 5.1 so I try some free **AC3s** [http://www.lynnemusic.com/surround.html](http://www.lynnemusic.com/surround.html), but that doesn't work either.

Now start to play with **PulseAudio**. I edit the config and add 4 channels as the default
```
gksudo gedit /etc/pulse/daemon.conf
# default-sample-channels = 4 # This is the line I add
gksudo /etc/init.d/pulseaudio restart
```
But when I check the controls and volume there's only 2 channels
```
pavucontrol &
pavumeter &
```
I try to restart pulseaudio manually
```
killall pulseaudio
pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround40:0
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround71:0
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
W: alsa-util.c: Device hw:0 doesn't support 4 channels, changed to 2.

```

Yet when I run the ALSA test again I can clearly hear that all 4 channels exist and work.
```
speaker-test -Dsurround40 -c4 -l1 -twav
```

I create ~/.asoundrc and put in this configuration:
```
pcm.ch40dup {
type route
slave.pcm surround40
slave.channels 4
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
}
```
I don't know if that's what fixed my problem or that I rebooted the computer a few times. After the rebooting I opened gnome-volume-control again and turned the volume for surround on and things seem to be working now. 

The next problem is that the surround **isn't synced** with the **master volume**. I fixed this by right-clicking on the **volume icon** and selected **Preferences**. I then used ctrl to select the multiple values Master, front, pcm, and surround. Next I close the window, saving the changes.

Now everything works. 
When I play the AC3 test I can hear that my speakers correctly upmix the center channel and bass.
I'm happy!





Resources:
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)
[http://ubuntuforums.org/showthread.php?t=243500](http://ubuntuforums.org/showthread.php?t=243500)
[http://www.lynnemusic.com/surround.html](http://www.lynnemusic.com/surround.html)

Additional info:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4780]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  ...
  Subdevice #31: subdevice #31
card 0: Live [SBLive! Value [CT4780]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  ...
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4780]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Note: SBLive! was supposed to be 5.1, but only certain models are. I have speakers that upmix from 4.0 to 5.1.
Applies to: CT4780 CT4870 CT4830

---

### Post by linuxwizard on 2009-01-03
You need to remove the comment from the beginning of this line > # default-sample-channels = 4. Also if you have 4.1 system change 4 to 5 if you have 5.1 system change 4 to 6.  

[http://www.pulseaudio.org/wiki/FAQ](http://www.pulseaudio.org/wiki/FAQ)

---

### Post by coolaj86 on 2009-01-03
I didn't actually put the # in when I put the line in, so it is as it should be.

---

### Post by linuxwizard on 2009-01-03
You have to remove comment. I gave the link to show that. I take it you didn't look it over. So here I copied it for you. Please Read It

Many people have a surround card, but have speakers for just two channels, so PulseAudio can't really default to a surround setup. To enable all the channels, edit /etc/pulse/daemon.conf: uncomment the default-sample-channels line (i.e. REMOVE the semicolon from the beginning of the line) and set the value to 6 if you have a 5.1 setup, or 8 if you have 7.1 setup etc. After doing the edit, restart pulseaudio.

---

### Post by coolaj86 on 2009-01-03
Yes, I did read that page, and yes that is the way that it is. Notice the output I posted of when I ran `pulseaudio`:

```
W: alsa-util.c: Device hw:0 doesn't support 4 channels, changed to 2.
```

It is set to use 4 channels but then went reverted to 2 when it starts. Yet the Alsa still plays fine.

I rebooted and then it was working for a few minutes in totem but I closed totem and re-opened it and was back to reporting 4 channels and using 2. Amarok didn't work either, but the ALSA test still works.

---

