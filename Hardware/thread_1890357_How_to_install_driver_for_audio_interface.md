---
title: "How to install driver for audio interface"
date: 2011-12-03
forum: Hardware
---

### Post by lintlicker on 2011-12-03
Hi,

I'm a musician.  I have an Edirol UA-4FX audio interface that I would like to install. An audio interface allows me to plug microphones, guitars, etc. directly into the computer via usb for recording.  I have used this device extensively in windows, but unfortunately my windows will not boot (which is why I've switched to ubuntu).

I LOVE how fast Ubuntu is, and I would love to completely abandon windows, but I need this device to work.  I still have very little understanding about how linux/ubuntu works, and I was wondering if it would be possible to install the drivers for this device.

Any help or advice would be greatly appreciated.

lintlicker

---

### Post by cbowman57 on 2011-12-03
What I see when I search for Edirol it brings up an app called mudita24, not sure if that will do what you want or not but worth a look.

You might find this forum useful: [http://www.linuxmusicians.com/viewtopic.php?f=6&t=3111](http://www.linuxmusicians.com/viewtopic.php?f=6&t=3111)

---

### Post by lintlicker on 2011-12-03
Thanks for the fast response. :)

I'm not sure what the link you provided me does, but it did lead me down a path that eventually led me to this: [http://ubuntuforums.org/showthread.php?t=1043691](http://ubuntuforums.org/showthread.php?t=1043691)
I discovered that my audio interface does function.  The only problem is that it does not function well.  Apparently I don't need to install any drivers...... weird.   The audio is crackly and audacity (the audio program I use) runs very slowly.

To be honest, I don't even know what questions I need to ask.  I'd really like to get a fast and stable audio recording program running.  Pretty much everything about Ubuntu is strange and alien to me though.

Yeah, really confused.  Help

:)

---

### Post by cbowman57 on 2011-12-03
> **lintlicker said:**
> Thanks for the fast response. :)

I'm not sure what the link you provided me does, but it did lead me down a path that eventually led me to this: [http://ubuntuforums.org/showthread.php?t=1043691](http://ubuntuforums.org/showthread.php?t=1043691)
I discovered that my audio interface does function.  The only problem is that it does not function well.  Apparently I don't need to install any drivers...... weird.   The audio is crackly and audacity (the audio program I use) runs very slowly.

To be honest, I don't even know what questions I need to ask.  I'd really like to get a fast and stable audio recording program running.  Pretty much everything about Ubuntu is strange and alien to me though.

Yeah, really confused.  Help

:)

Ok, cool.  Is your hardware pretty capable (quick with decent processing power)? 

Now I'm gonna send you down the rabbit hole of tuning pulseaudio. :)

I'm going to give you a couple of links, apply what seems to make sense, it's going to refer you to changes in your  daemon.conf, default.pa & .asoundrc.  When you get done with as much as you are comfortable with please post the current state of those files enclosed in [code] boxes. (Might want to do 3 separate posts.)

[http://wiki.audacityteam.org/index.php?title=Linux_Issues]("htthttp://wiki.audacityteam.org/index.php?title=Linux_Issuesp://")
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
[https://wiki.archlinux.org/index.php/PulseAudio](https://wiki.archlinux.org/index.php/PulseAudio)

---

### Post by lintlicker on 2011-12-03
My hardware should be plenty capable.  I have like 4Gb of ram.  I'm a little concerned about the state of my hard drive.  I have a broken windows installed, and now I have multiple copies of things like java, flash, etc.  I'd like to shrink windows eventually somehow, but one thing at a time.

I will follow the links as best I can and report back.

Thank you again.

---

### Post by cbowman57 on 2011-12-03
Good deal, no promises but we'll see what we can do

What I've discovered on my system is that default pulseaudio is pretty crappy, but I think we can fix that for you.

---

### Post by lintlicker on 2011-12-04
Reaction to audacity link:

Mostly confused, got two avenues for exploration:
1) record in stereo.
        I can't seem to be able to figure out how to make audacity do this.  I haven't had breakfast yet, so I'm too impatient to try too hard.
2) Use JACK
        Now this is WAY over my head.  I feel like I'm missing some key information/language about understanding linux/ubuntu.  Not the least of which is that there's like 17 different ways to install programs, most of which are complex and hard to make work.  The only reliable way I've found to install stuff is to use the Ubuntu Software Center.
        I ragequit my efforts to use JACK, mostly because I don't even know if it can solve my problem.

---

### Post by lintlicker on 2011-12-04
My reaction to both Pulse Audio links,

I am so sorry, but I really don't know what I'm doing.  My windows mindset does not compute most/all of the content here.  I've installed pulse audio via the ubuntu software center.  I don't know what it is supposed to do.

WAIT!  PROGRESS!  (I had the brilliant idea to test audacity before complaining)

Audacity is recording in stereo, and sound quality is improved INCREDIBLY!  I can record one track and it sounds pretty perfect.  When I record a second track, there's still quality issues, but they're MUCH better, but still needs work.

So, pulse audio must have done something.  I'm still so confused.

---

### Post by cbowman57 on 2011-12-04
It is confusing, but not insurmountable.

Ok, let me see the 3 files I mentioned in previous post.  We may have to create the ~/.asoundrc (~/ = /home/yourusername) the . in front of asoundrc makes it a hidden file, so using nautilus, your file browser, navigate to your home directory and press ctl+h, that will toggle your hidden files visible. It will also hide them again.

Ok, we're going to just create that file if it doesn't already exist, if it does exist we're going to wipe it clean & paste this inside it. 

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```I need to see that daemon.conf & the default.pa (they can be found in  /etc/pulse )

---

### Post by lintlicker on 2011-12-04
Should I attach the files or post the contents in [code] boxes?

---

### Post by cbowman57 on 2011-12-04
Please, just post them in code boxes. :)

---

### Post by lintlicker on 2011-12-04
Ok.

Daemon.conf
```
;daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10
```and default.pa
```

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

---

### Post by cbowman57 on 2011-12-04
Ok, hopefully you don't have a really odd collection of hardware.

Let's start with the default.pa, looks good as is, if we get some choppiness or glitches later we might change **load-module module-udev-detect**  to [COLOR=Red]**load-module module-udev-detect tsched=0**[/COLOR] [COLOR=Black]but for now we'll let it ride.

Alright, daemon.conf:

Uncomment (remove ";")  [/COLOR]
; nice-level = -11
and change the value to something like -3
```
 nice-level = -3
```This is to give pulseaudio some cpu priority without making the system sluggish in the process.  You may want to experiment with that value in the -1 to -11 range.

Change your resample method, the first example that is commented out here is super quality but will tax your cpu so it's hardware dependent, if you're going to do commercial quality recording & your system is dedicated to your studio you might want to us that one. speex-float-9 is less resource intensive & you proably won't be able to hear the difference 
```

; resample-method=src-sinc-best-quality
resample-method = speex-float-9 
```For your needs we may also need to uncomment these & change one or both to **yes**, just keep it for reference ```
; enable-remixing = yes
; enable-lfe-remixing = no
```Now we're going to try improving sound quality some more.  Try this ```
default-sample-format = float32le
```Next try ```
default-sample-rate = 96000 
``` if that seems like overkill you can always try a value of 48000

This should get you started, this isn't definitive or final but should make for a good starting point.  Assuming there isn't a problem your music should be only limited by the capabilities of your speakers.  I don't have high dollar speakers but the sound quality went from decent radio quality to that of a home stereo.

Let's give that a go.

Personally I don't think they put as much emphasis on configuring pulseaudio as they should, the criticism extend to Windows too, not sure about Macs.

---

### Post by lintlicker on 2011-12-04
Ok, I've made the changes to a copy of daemon.conf, but I can't figure out how to put it into the /etc/pulse location.  It just doesn't let me alter the contents of that folder at all.

What do I do?

---

### Post by cbowman57 on 2011-12-04
> **lintlicker said:**
> Ok, I've made the changes to a copy of daemon.conf, but I can't figure out how to put it into the /etc/pulse location.  It just doesn't let me alter the contents of that folder at all.

What do I do?

Ok, easiest way is to use nautilus as root.  Either hit alt+f2 to run a command or open a terminal and use **gksu nautilus**.  Then you can just cut, copy, paste, whatever with root privileges.

The heightened security is something you will have to become accustomed to if you stick with Linux.

---

### Post by lintlicker on 2011-12-04
Holy cow that was a fast response.  Personally, I like the high security.  Makes me feel like I can't mess anything up unless I REALLY want to.  Job done.  Gonna reboot and try it.

---

### Post by cbowman57 on 2011-12-04
> **lintlicker said:**
> Holy cow that was a fast response.  Personally, I like the high security.  Makes me feel like I can't mess anything up unless I REALLY want to.  Job done.  Gonna reboot and try it.

And? :)

I guess the most important question, do you still at least have sound?

---

### Post by lintlicker on 2011-12-04
Ok, the problem is still there, it's just a much higher quality problem.  Recording one track sounds fine, but recording a second track causes it to, well it's hard to explain.  I made an mp3, but I can't seem to be able to post it here.

I made a filefreak account (seems dubious, but if it works, whatever) I think it should work.
[http://www.filefreak.com/files/850434_f7oab/littlebawxes.mp3](http://www.filefreak.com/files/850434_f7oab/littlebawxes.mp3)

You will clearly be able to hear which track is good and which track is weird.  It's like it cuts in and out several times per second.

---

### Post by cbowman57 on 2011-12-04
> **lintlicker said:**
> Ok, the problem is still there, it's just a much higher quality problem.  Recording one track sounds fine, but recording a second track causes it to, well it's hard to explain.  I made an mp3, but I can't seem to be able to post it here.

I made a filefreak account (seems dubious, but if it works, whatever) I think it should work.
[http://www.filefreak.com/files/850434_f7oab/littlebawxes.mp3](http://www.filefreak.com/files/850434_f7oab/littlebawxes.mp3)

You will clearly be able to hear which track is good and which track is weird.  It's like it cuts in and out several times per second.

How's playback quality of the audio files you didn't record with it?

Take another look at this [https://wiki.archlinux.org/index.php/PulseAudio](https://wiki.archlinux.org/index.php/PulseAudio) under the ALSA Monitor source heading.

I don't do any recording so I'm probably leaving my comfort zone now.  I know there is a thread and/or forum for musicians that use linux.  You might have to explore that for answers that are better tailored to what you are doing.

You can also go back over some of the initial links I posted & see if there is anything that jumps out at you & just makes sense.  I've tried some generic suggestions but your hardware may dictate some other changes.

The stutter/warbling might be due to some other process interrupting pulseaudio.  You may want to try other nice values, or comment that line again & I think it will default back to -11.  (Don't be fooled by the negative number, that indicates how NOT nice it is)

Oh, you don't need to reboot between changes to these configuration files, just **pulseaudio -k** in a terminal will stop & restart it.

---

### Post by lintlicker on 2011-12-05
I think I'll consult linux musicians.com then.  Thank you for all your help.

---

### Post by cbowman57 on 2011-12-05
> **lintlicker said:**
> I think I'll consult linux musicians.com then.  Thank you for all your help.

Probably for the best. :)

---

