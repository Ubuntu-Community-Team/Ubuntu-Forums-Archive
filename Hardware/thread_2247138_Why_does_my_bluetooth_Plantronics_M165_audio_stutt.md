---
title: "Why does my bluetooth Plantronics M165 audio stutter in linux (ubuntu 14.04)?"
date: 2014-10-05
forum: Hardware
---

### Post by neek-w on 2014-10-05
I'm running Ubuntu 14.04 (fresh install a few months ago), kernel 3.13.0-36-generic, all recent updates installed.  I posted this question over at Plantronics site ([http://soundingboard.plantronics.com/message/46229#46229](http://soundingboard.plantronics.com/message/46229#46229)) but I thought reaching out to the Ubuntu community itself would be more productive.  Here's the post:

I'm the proud new owner of an M165  bluetooth headset.  It pairs and works perfectly with my Android phone  (Nexus 5).  However in Linux (Ubuntu 14.04 on a Toshiba Satellite L840  64 bit) it pairs but the audio stutters.
 
That  is, once I get the device paired, connected, and selected as the output  device, I get audio but it will pause for a 10th of a second about  every second.
 
This laptop runs PulseAudio and there are a few quirks of operation that I don't fully understand.
- The bluetooth task bar widget works fine, has a "PLTM165" menu dropdown that lets me easily connect/disconnect the headset.
- After connection, sometimes the headset does not appear in the default system audio control panel.
-  Sometimes the list of input and output devices in the audio control  panel is completely empty.  Even the usual Output devices  "HDMI/DisplayPort" and "Speakers - Built-in Audio" have disappeared.
-  Running the command "gksudo pactl load-module  module-bluetooth-discover" does seem to help the audio device appear  sometimes.  It seems the default setup loaded by the bluetooth system  either doesn't have this module, or the magic performed by this command  isn't executed properly when the device is connected.
 
I notice a stream of messages like this in my syslog:
 
```
Oct  5 18:23:14 localhost kernel: [ 1461.772178] Bluetooth: hci0 SCO packet for unknown connection handle 63487

Oct  5 18:23:14 localhost kernel: [ 1461.782184] Bluetooth: hci0 SCO packet for unknown connection handle 65498
Oct  5 18:23:14 localhost kernel: [ 1461.792139] Bluetooth: hci0 SCO packet for unknown connection handle 65506
Oct  5 18:23:14 localhost kernel: [ 1461.792147] Bluetooth: hci0 SCO packet for unknown connection handle 3072
Oct  5 18:23:14 localhost kernel: [ 1461.792150] Bluetooth: hci0 SCO packet for unknown connection handle 10


``` 
They appear rapidly as soon as I start output (e.g. play radio in Rhythmbox) and stop when the playback stops.
 
After  stopping playback, I used the bluetooth system tray icon to disconnect,  then reconnect the headset.  The headset spoke "Phone 2 disconnected"  and "connected" properly, then the following syslog messages were  generated:
 
```
Oct  5 18:23:15 localhost kernel: [ 1462.993458] Bluetooth: hci0 SCO packet for unknown connection handle 65504

Oct  5 18:23:15 localhost kernel: [ 1462.993461] Bluetooth: hci0 SCO packet for unknown connection handle 6144
Oct  5 18:23:15 localhost kernel: [ 1462.993464] Bluetooth: hci0 SCO packet for unknown connection handle 38
Oct  5 18:23:15 localhost kernel: [ 1462.993466] Bluetooth: hci0 SCO packet for unknown connection handle 9728
Oct  5 18:23:15 localhost bluetoothd[574]: message repeated 7 times: [ Audio connection got disconnected]
Oct  5 18:24:19 localhost bluetoothd[574]: Discover: Connection timed out (110)
Oct  5 18:24:23 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally
Oct   5 18:24:23 localhost pulseaudio[4313]: message repeated 10 times: [  [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally]
Oct  5 18:24:28 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] ratelimit.c: 115 events suppressed
Oct  5 18:24:28 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally
Oct   5 18:24:28 localhost pulseaudio[4313]: message repeated 10 times: [  [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally]
Oct  5 18:24:33 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] ratelimit.c: 115 events suppressed
Oct  5 18:24:33 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally
Oct   5 18:24:33 localhost pulseaudio[4313]: message repeated 10 times: [  [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally]
Oct   5 18:24:38 localhost pulseaudio[4313]: [pulseaudio]  module-bluetooth-device.c: Failed to acquire transport  /org/bluez/574/hci0/dev_0C_E0_E4_32_46_A8/fd2
Oct  5 18:24:44 localhost bluetoothd[574]: Connection reset by peer (104)
Oct  5 18:24:48 localhost bluetoothd[574]: Unable to select SEP
Oct  5 18:24:48 localhost kernel: [ 1556.278741] input: 0C:E0:E4:32:46:A8 as /devices/virtual/input/input20
Oct   5 18:24:38 localhost pulseaudio[4313]: [pulseaudio]  module-bluetooth-device.c: Failed to acquire transport  /org/bluez/574/hci0/dev_0C_E0_E4_32_46_A8/fd2
Oct  5 18:24:57 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] ratelimit.c: 956 events suppressed
Oct  5 18:24:57 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally
Oct   5 18:24:57 localhost pulseaudio[4313]: message repeated 10 times: [  [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally]
Oct  5 18:25:02 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] ratelimit.c: 115 events suppressed
Oct  5 18:25:02 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally
Oct   5 18:25:02 localhost pulseaudio[4313]: message repeated 10 times: [  [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally]
Oct  5 18:25:07 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] ratelimit.c: 115 events suppressed
Oct  5 18:25:07 localhost pulseaudio[4313]: [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally
Oct   5 18:25:07 localhost pulseaudio[4313]: message repeated 10 times: [  [alsa-source-ID 506e Analog] asyncq.c: q overrun, queuing locally]
Oct   5 18:25:11 localhost pulseaudio[4313]: [pulseaudio]  module-bluetooth-device.c: Failed to acquire transport  /org/bluez/574/hci0/dev_0C_E0_E4_32_46_A8/fd3
Oct  5 18:25:12 localhost kernel: [ 1580.321448] input: 0C:E0:E4:32:46:A8 as /devices/virtual/input/input21
Oct  5 18:25:12 localhost bluetoothd[574]: Unable to select SEP
Oct  5 18:25:26 localhost bluetoothd[574]: HUP or ERR on socket
Oct  5 18:25:32 localhost NetworkManager[910]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Oct  5 18:27:08 localhost AptDaemon: INFO: Quitting due to inactivity
Oct  5 18:27:08 localhost AptDaemon: INFO: Quitting was requested


``` 
Note  that it did eventually connect ("kernel: [ 1556.278741] input:  0C:E0:E4:32:46:A8 as /devices/virtual/input/input20") but the overrun  log continued.
 
I've followed advice at [http://ubuntuforums.org/showthread.php?t=1979191&page=4](http://ubuntuforums.org/showthread.php?t=1979191&page=4) which adds a line to /etc/modprobe.d/alsa-base.conf but I'm not even sure I have that audio card chipset.
 
I've tried various combinations of rebooting and running that pactl command before and after connecting the device.
 
I'm  at a loss what to run to further investigate this.  Any advice or  investigative commands I should run would be welcome.  I'm going to have  to use this headset with my phone for now which is far from ideal.
 
Nick

---

### Post by jacobmar1ey on 2014-10-14
I have this same problem
```

Oct 14 11:25:59 iridium kernel: [82586.157951] Bluetooth: hci0 SCO packet for unknown connection handle 1
Oct 14 11:25:59 iridium kernel: [82586.167960] Bluetooth: hci0 SCO packet for unknown connection handle 9
Oct 14 11:25:59 iridium kernel: [82586.187983] Bluetooth: hci0 SCO packet for unknown connection handle 64768
Oct 14 11:25:59 iridium kernel: [82586.197986] Bluetooth: hci0 SCO packet for unknown connection handle 65534
Oct 14 11:25:59 iridium kernel: [82586.197990] Bluetooth: hci0 SCO packet for unknown connection handle 1280
Oct 14 11:25:59 iridium kernel: [82586.197991] Bluetooth: hci0 SCO packet for unknown connection handle 65530
Oct 14 11:25:59 iridium kernel: [82586.218027] Bluetooth: hci0 SCO packet for unknown connection handle 65528
Oct 14 11:25:59 iridium kernel: [82586.228051] Bluetooth: hci0 SCO packet for unknown connection handle 65535
Oct 14 11:25:59 iridium kernel: [82586.228054] Bluetooth: hci0 SCO packet for unknown connection handle 1792
Oct 14 11:25:59 iridium kernel: [82586.248049] Bluetooth: hci0 SCO packet for unknown connection handle 65531
Oct 14 11:25:59 iridium kernel: [82586.248053] Bluetooth: hci0 SCO packet for unknown connection handle 256
Oct 14 11:25:59 iridium kernel: [82586.248054] Bluetooth: hci0 SCO packet for unknown connection handle 1
Oct 14 11:25:59 iridium kernel: [82586.248055] Bluetooth: hci0 SCO packet for unknown connection handle 65535
Oct 14 11:25:59 iridium kernel: [82586.248056] Bluetooth: hci0 SCO packet for unknown connection handle 2304
Oct 14 11:25:59 iridium kernel: [82586.258045] Bluetooth: hci0 SCO packet for unknown connection handle 6
Oct 14 11:25:59 iridium kernel: [82586.258050] Bluetooth: hci0 SCO packet for unknown connection handle 2560
Oct 14 11:25:59 iridium kernel: [82586.258052] Bluetooth: hci0 SCO packet for unknown connection handle 7
Oct 14 11:25:59 iridium kernel: [82586.258053] Bluetooth: hci0 SCO packet for unknown connection handle 2047
Oct 14 11:25:59 iridium kernel: [82586.278053] Bluetooth: hci0 SCO packet for unknown connection handle 8
Oct 14 11:25:59 iridium kernel: [82586.288122] Bluetooth: hci0 SCO packet for unknown connection handle 64256
Oct 14 11:25:59 iridium kernel: [82586.308097] Bluetooth: hci0 SCO packet for unknown connection handle 65529
Oct 14 11:25:59 iridium kernel: [82586.308102] Bluetooth: hci0 SCO packet for unknown connection handle 8
Oct 14 11:25:59 iridium kernel: [82586.308104] Bluetooth: hci0 SCO packet for unknown connection handle 2304
Oct 14 11:25:59 iridium kernel: [82586.308106] Bluetooth: hci0 SCO packet for unknown connection handle 10
Oct 14 11:25:59 iridium kernel: [82586.318087] Bluetooth: hci0 SCO packet for unknown connection handle 7
Oct 14 11:25:59 iridium kernel: [82586.338106] Bluetooth: hci0 SCO packet for unknown connection handle 63743
Oct 14 11:25:59 iridium kernel: [82586.338109] Bluetooth: hci0 SCO packet for unknown connection handle 65530
Oct 14 11:25:59 iridium kernel: [82586.338111] Bluetooth: hci0 SCO packet for unknown connection handle 3840
Oct 14 11:25:59 iridium kernel: [82586.348111] Bluetooth: hci0 SCO packet for unknown connection handle 12
Oct 14 11:25:59 iridium kernel: [82586.368195] Bluetooth: hci0 SCO packet for unknown connection handle 65524
Oct 14 11:25:59 iridium kernel: [82586.368198] Bluetooth: hci0 SCO packet for unknown connection handle 0
Oct 14 11:25:59 iridium kernel: [82586.378148] Bluetooth: hci0 SCO packet for unknown connection handle 5
Oct 14 11:25:59 iridium kernel: [82586.398236] Bluetooth: hci0 SCO packet for unknown connection handle 64256
Oct 14 11:25:59 iridium kernel: [82586.398242] Bluetooth: hci0 SCO packet for unknown connection handle 16
Oct 14 11:25:59 iridium kernel: [82586.398244] Bluetooth: hci0 SCO packet for unknown connection handle 6
Oct 14 11:25:59 iridium kernel: [82586.418211] Bluetooth: hci0 SCO packet for unknown connection handle 65521
Oct 14 11:25:59 iridium kernel: [82586.418217] Bluetooth: hci0 SCO packet for unknown connection handle 768
Oct 14 11:25:59 iridium kernel: [82586.428180] Bluetooth: hci0 SCO packet for unknown connection handle 5
Oct 14 11:25:59 iridium kernel: [82586.448202] Bluetooth: hci0 SCO packet for unknown connection handle 65023
Oct 14 11:25:59 iridium kernel: [82586.448205] Bluetooth: hci0 SCO packet for unknown connection handle 65527
Oct 14 11:25:59 iridium kernel: [82586.448206] Bluetooth: hci0 SCO packet for unknown connection handle 1535
Oct 14 11:25:59 iridium kernel: [82586.448208] Bluetooth: hci0 SCO packet for unknown connection handle 6
Oct 14 11:25:59 iridium kernel: [82586.448209] Bluetooth: hci0 SCO packet for unknown connection handle 7936
Oct 14 11:25:59 iridium kernel: [82586.448210] Bluetooth: hci0 SCO packet for unknown connection handle 1072
Oct 14 11:25:59 iridium kernel: [82586.448211] Bluetooth: hci0 SCO packet for unknown connection handle 13
Oct 14 11:25:59 iridium kernel: [82586.458207] Bluetooth: hci0 SCO packet for unknown connection handle 14
Oct 14 11:25:59 iridium kernel: [82586.458210] Bluetooth: hci0 SCO packet for unknown connection handle 3584
Oct 14 11:25:59 iridium kernel: [82586.458212] Bluetooth: hci0 SCO packet for unknown connection handle 65528
Oct 14 11:25:59 iridium kernel: [82586.478198] Bluetooth: hci0 SCO packet for unknown connection handle 4
Oct 14 11:25:59 iridium kernel: [82586.478205] Bluetooth: hci0 SCO packet for unknown connection handle 65533
Oct 14 11:25:59 iridium kernel: [82586.478208] Bluetooth: hci0 SCO packet for unknown connection handle 2560
Oct 14 11:25:59 iridium kernel: [82586.478211] Bluetooth: hci0 SCO packet for unknown connection handle 13
Oct 14 11:25:59 iridium kernel: [82586.478214] Bluetooth: hci0 SCO packet for unknown connection handle 3
Oct 14 11:25:59 iridium kernel: [82586.498246] Bluetooth: hci0 SCO packet for unknown connection handle 65533
Oct 14 11:25:59 iridium kernel: [82586.508247] Bluetooth: hci0 SCO packet for unknown connection handle 64767
Oct 14 11:25:59 iridium kernel: [82586.508250] Bluetooth: hci0 SCO packet for unknown connection handle 0
Oct 14 11:25:59 iridium kernel: [82586.508251] Bluetooth: hci0 SCO packet for unknown connection handle 3120
Oct 14 11:25:59 iridium kernel: [82586.528262] Bluetooth: hci0 SCO packet for unknown connection handle 6
Oct 14 11:25:59 iridium kernel: [82586.538273] Bluetooth: hci0 SCO packet for unknown connection handle 63231
Oct 14 11:25:59 iridium kernel: [82586.558298] Bluetooth: hci0 SCO packet for unknown connection handle 2
Oct 14 11:25:59 iridium kernel: [82586.558303] Bluetooth: hci0 SCO packet for unknown connection handle 3072
Oct 14 11:25:59 iridium kernel: [82586.558304] Bluetooth: hci0 SCO packet for unknown connection handle 3
Oct 14 11:25:59 iridium kernel: [82586.558305] Bluetooth: hci0 SCO packet for unknown connection handle 2
Oct 14 11:25:59 iridium kernel: [82586.568300] Bluetooth: hci0 SCO packet for unknown connection handle 64000
Oct 14 11:25:59 iridium kernel: [82586.588320] Bluetooth: hci0 SCO packet for unknown connection handle 65516
Oct 14 11:25:59 iridium kernel: [82586.588323] Bluetooth: hci0 SCO packet for unknown connection handle 65531
Oct 14 11:25:59 iridium kernel: [82586.588325] Bluetooth: hci0 SCO packet for unknown connection handle 65533
Oct 14 11:25:59 iridium kernel: [82586.588326] Bluetooth: hci0 SCO packet for unknown connection handle 8191
Oct 14 11:25:59 iridium kernel: [82586.588327] Bluetooth: hci0 SCO packet for unknown connection handle 2352
Oct 14 11:25:59 iridium kernel: [82586.588328] Bluetooth: hci0 SCO packet for unknown connection handle 10
Oct 14 11:25:59 iridium kernel: [82586.608349] Bluetooth: hci0 SCO packet for unknown connection handle 65533
Oct 14 11:25:59 iridium kernel: [82586.608352] Bluetooth: hci0 SCO packet for unknown connection handle 1792
Oct 14 11:25:59 iridium kernel: [82586.608354] Bluetooth: hci0 SCO packet for unknown connection handle 65521
Oct 14 11:25:59 iridium kernel: [82586.618346] Bluetooth: hci0 SCO packet for unknown connection handle 65280
Oct 14 11:25:59 iridium kernel: [82586.618349] Bluetooth: hci0 SCO packet for unknown connection handle 16
Oct 14 11:25:59 iridium kernel: [82586.618351] Bluetooth: hci0 SCO packet for unknown connection handle 48
Oct 14 11:25:59 iridium kernel: [82586.638408] Bluetooth: hci0 SCO packet for unknown connection handle 65531
Oct 14 11:25:59 iridium kernel: [82586.638414] Bluetooth: hci0 SCO packet for unknown connection handle 304
Oct 14 11:25:59 iridium kernel: [82586.648371] Bluetooth: hci0 SCO packet for unknown connection handle 17

```

Note that is all posted in ONE SECOND to syslog. My headset works, and is sometimes choppy, but this is clearly not okay and my computer went into a hard freeze a few minutes ago. If anyone has ideas what to do with this it'd be great. I'm on a plantronics M55 headset, by the way.

---

