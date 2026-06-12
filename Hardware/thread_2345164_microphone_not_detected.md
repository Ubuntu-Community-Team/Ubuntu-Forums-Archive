---
title: "microphone not detected"
date: 2016-12-01
forum: Hardware
---

### Post by gio-mond on 2016-12-01
Hi!

I'm using ubuntu 16.04 on cubi, a mini pc from msi ([https://www.msi.com/Desktop/Cubi.html.html#hero-overview](https://www.msi.com/Desktop/Cubi.html.html#hero-overview)). It has a line in/out, as shown in the picture at the following link ([https://asset.msi.com/global/picture/image/feature/desktop/cubi/cubi_12.jpg](https://asset.msi.com/global/picture/image/feature/desktop/cubi/cubi_12.jpg)).

I inserted a microphone in the line in/out, but unfortunately it's not detected (I tried the microphone on another pc and it works).

This is alsamixer:

[ATTACH=CONFIG]272480[/ATTACH]

Can anyone give me advice? What can I try?

Thank you!

---

### Post by gordintoronto on 2016-12-01
If there is a single socket for in and out, it might be looking for a headset rather than a single device.

---

### Post by gio-mond on 2016-12-02
> **gordintoronto said:**
> If there is a single socket for in and out, it might be looking for a headset rather than a single device.

I tried with a headset, but only the output works.

I also tried to add the line 
```
options snd-hda-intel model=dell-headset-multi
```
 in /etc/modprobe.d/alsa-base.conf, as suggested [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1420988"), but it didn't work.

---

### Post by gio-mond on 2016-12-02
And I also tried to reassign pin 0x18 to microphone with hdajackretask, as suggested [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1359803"). 

After doing this, alsamixer shows the microphone:

[ATTACH=CONFIG]272513[/ATTACH]

But pulseaudio says the microphone is still unplagged.
[ATTACH=CONFIG]272512[/ATTACH]

Indeed, it still does not record.

---

### Post by gio-mond on 2016-12-02
Does anyone use Realtek ALC283?
If yes, please share your configuration.

---

### Post by gio-mond on 2016-12-02
Some more details, just in case someone can enlighten me.

Pulseaudio tells that the headphone are plugged in even when I insert the microphone.
Now my question is: since the jack of a headphone and a microphone are basically the same, how the system can know I inserted a microphone?

---

### Post by #&amp;thj^% on 2016-12-02
Not sure I can help but lets take a crack at this.
Return the output of this from the terminal:
```
arecord -l
```
Paste back here and Please use Code tags it is easier to read.

---

### Post by gio-mond on 2016-12-02
the output of arecord -l is
```
**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: ALC283 Alt Analog [ALC283 Alt Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
```

---

### Post by #&amp;thj^% on 2016-12-02
Ok Lets Edit this file:
```
sudo -H gedit /etc/pulse/default.pa
```
Add this line as described below:
```
load-module module-alsa-source device=hw:0,0
  # the line above should be somewhere before the line below
 .ifexists module-udev-detect.so
```

Now restart pulseaudio to apply the new settings: 

```
pulseaudio -k ; pulseaudio -D
```

If everything worked correctly, you should now see your mic show up when running pavucontrol (under the Input Devices tab).
If not check again with alsamixer and toggle to see if it there with F6
I would comment out the line you had already added previously though...just to make sure nothing else is fowling it up.
So it would look like this now:
```
# options snd-hda-intel model=dell-headset-multi
```
Sometimes it even takes a reboot to take effect.

---

### Post by gio-mond on 2016-12-02
ok, this is the file you told me to edit:

```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
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
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

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

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
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
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

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

load-module module-alsa-source device=hw:0,0
  # the line above should be somewhere before the line below
 .ifexists module-udev-detect.so
```

I inserted the new three lines at the end.

When I run pavucontrol, I obtain this:

[ATTACH=CONFIG]272522[/ATTACH]

I tried to start it manually and this is the result:
```
giovanni@giovanni-MS-B09611:~$ start-pulseaudio-x11
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```

---

### Post by gio-mond on 2016-12-03
Hi guys!

I reverted to the original version of /etc/pulse/default.pa, because of the problem shown in my previous post.

Then I kept on trying with hdajackretask.
Well, overriding pin 0x19 from "not connected" to "microphone", finally the microphone of the headset works.

Can someone explain me if plugging in an headset is the only way to have a microphone working with a combo jack?
I would like to use a stand-alone microphone (not an headset), since it has a better quality than the microphone of the headset. Is there any chance? (without buying a jack splitter)

---

### Post by #&amp;thj^% on 2016-12-03
> **gio-mond said:**
> ok, this is the file you told me to edit:

```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/freedesktop/stereo/bell.oga
#load-sample-lazy pulse-hotplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-coldplug /usr/share/sounds/freedesktop/stereo/device-added.oga
#load-sample-lazy pulse-access /usr/share/sounds/freedesktop/stereo/message.oga

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
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
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

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

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
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
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
#load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

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

load-module module-alsa-source device=hw:0,0
  # the line above should be somewhere before the line below
 .ifexists module-udev-detect.so
```

I inserted the new three lines at the end.

When I run pavucontrol, I obtain this:

[ATTACH=CONFIG]272522[/ATTACH]

I tried to start it manually and this is the result:
```
giovanni@giovanni-MS-B09611:~$ start-pulseaudio-x11
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```

That was not the correct place:D sorry if this was unclear.
Pulseaudio is kind of flakey..._**and if you want to try again.**_..see if this edit works any better:
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, see <http://www.gnu.org/licenses/>.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Should be after module-*-restore but before module-*-detect
load-module module-switch-on-port-available

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

[COLOR=#008000]### Automatically load driver modules depending on the hardware available
load-module module-alsa-source device=hw:0,0
.ifexists module-udev-detect.so
load-module module-udev-detect
.else[/COLOR]
### Use the static hardware detection module (for systems that lack udev support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect channels=2
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

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

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
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
.ifexists module-console-kit.so
load-module module-console-kit
.endif
.ifexists module-systemd-login.so
load-module module-systemd-login
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music/video streams when a phone stream is active
load-module module-role-cork

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

### Make some devices default
#set-default-sink output
#set-default-source input
```
I used a different color to point to the difference with your first edit.
Headsets can be a challenge with pulseaudio to be sure.;)

---

### Post by gio-mond on 2016-12-03
Oh, I really misunderstood your previous instructions...

I tried with the new edit, but when I run pavucontrol I get the same message as post #10.

---

### Post by #&amp;thj^% on 2016-12-03
Ok then...Navigate to /home/<your-username>/.config/pulse   ### where <your-username> is your user name
And delete all the files there...and log out and back in again

---

### Post by gio-mond on 2016-12-03
> **1fallen said:**
> Ok then...Navigate to /home/<your-username>/.config/pulse   ### where <your-username> is your user name
And delete all the files there...and log out and back in again

Still the same message...

---

### Post by #&amp;thj^% on 2016-12-03
How are you starting pulseaudio...I just noticed you were using this command "start-pulseaudio-x11"  which will throw that error you are seeing "Failure: Module initialization failed"
Use my previous suggestions:
```
pulseaudio -k ; pulseaudio -D
```
Or even this:
```
pulseaudio --start
```

---

### Post by gio-mond on 2016-12-04
> **1fallen said:**
> How are you starting pulseaudio...I just noticed you were using this command "start-pulseaudio-x11"  which will throw that error you are seeing "Failure: Module initialization failed"
Use my previous suggestions:
```
pulseaudio -k ; pulseaudio -D
```
Or even this:
```
pulseaudio --start
```

This is what I did:
- editing /etc/pulse/default.pa
- deleting files contained in /home/<your-username>/.config/pulse
- restarting the system
- running pavucontrol from terminal, then obtaining the message already posted in #10
Since the message suggests to run start-pulseaudio-X11 manually, so I did... with the result of post #10

---

