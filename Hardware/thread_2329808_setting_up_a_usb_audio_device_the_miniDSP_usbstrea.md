---
title: "setting up a usb audio device: the miniDSP usbstreamer b"
date: 2016-07-05
forum: Hardware
---

### Post by delooper on 2016-07-05
Greetings, 

I am trying to set up a usb audio device on an Ubuntu box.  The idea is for it to be a music server for a stereo system. 

What I have done so far:

 * I can play music to the device via MPlayer -> Jack -> ALSA -> usbstreamer -> miniDSP -> amps -> speakers.  I am using .jack-plumbing:

```
[COLOR=#111111][FONT=Consolas](connect "MPlayer \[[0-9]+\]:out_0" "system:playback_9")
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas](connect "MPlayer \[[0-9]+\]:out_1" "system:playback_10")[/FONT][/COLOR]
```

.jackrc

```
/usr/bin/jackd -v -dalsa -dhw:USBStreamer -r44100 -p1024 -n2
```

 * I can get the ALSA speaker-test to play sounds on the device. ```
speaker-test -c 10 -t sin -F S32_LE -D front:USBStreamer
``` works. 

 * I can get MPD to play music locally on the device i.e. the built-in speakers, and I can control MPD via my Android phone.

What I have not been able to do is play music on the stereo system via MPD -> ALSA -> USBStreamer.  

I think the main problem is that the usbstreamer has 10 input channels.  Only channels 8 and 9 (indexed 0,1,...,9) are the left and right speaker channels.  This is some peculiarity having to do with the USBStreamer producing a TOSLink output. 

The item I find most enticing is this part of the /var/lib/alsa/asound.state file:

```
state.USBStreamer {control.1 {
    iface PCM
    name 'Playback Channel Map'
    value.0 0
    value.1 0
    value.2 0
    value.3 0
    value.4 0
    value.5 0
    value.6 0
    value.7 0
    value.8 0
    value.9 0
    comment {
        access read
        type INTEGER
        count 10
        range '0 - 36'
    }
}
control.2 {
    iface PCM
    name 'Capture Channel Map'
    value.0 0
    value.1 0
    value.2 0
    value.3 0
    value.4 0
    value.5 0
    value.6 0
    value.7 0
    value.8 0
    value.9 0
    comment {
        access read
        type INTEGER
        count 10
        range '0 - 36'
    }
}
control.3 {
    iface MIXER
    name 'USBStreamer Output Playback Switch'
    value.0 true
    value.1 true
    value.2 true
    value.3 true
    value.4 true
    value.5 true
    value.6 true
    value.7 true
    value.8 true
    value.9 true
    comment {
        access 'read write'
        type BOOLEAN
        count 10
    }
}
control.4 {
    iface MIXER
    name 'USBStreamer Output Playback Switch'
    index 1
    value true
    comment {
        access 'read write'
        type BOOLEAN
        count 1
    }
}
control.5 {
    iface MIXER
    name 'USBStreamer Output Playback Volume'
    value.0 255
    value.1 255
    value.2 255
    value.3 255
    value.4 255
    value.5 255
    value.6 255
    value.7 255
    value.8 255
    value.9 255
    comment {
        access 'read write'
        type INTEGER
        count 10
        range '0 - 255'
        dbmin -12750
        dbmax 0
        dbvalue.0 0
        dbvalue.1 0
        dbvalue.2 0
        dbvalue.3 0
        dbvalue.4 0
        dbvalue.5 0
        dbvalue.6 0
        dbvalue.7 0
        dbvalue.8 0
        dbvalue.9 0
    }
}
control.6 {
    iface MIXER
    name 'USBStreamer Output Playback Volume'
    index 1
    value 152
    comment {
        access 'read write'
        type INTEGER
        count 1
        range '0 - 255'
        dbmin -12750
        dbmax 0
        dbvalue.0 -5150
    }
}
control.7 {
    iface MIXER
    name 'USBStreamer Clock Selector'
    value 'USBStreamer Internal Clock'
    comment {
        access 'read write'
        type ENUMERATED
        count 1
        item.0 'USBStreamer Internal Clock'
        item.1 'USBStreamer TOSLINK Clock'
    }
}
control.8 {
    iface MIXER
    name 'Mic Capture Switch'
    value.0 true
    value.1 true
    value.2 true
    value.3 true
    value.4 true
    value.5 true
    value.6 true
    value.7 true
    value.8 true
    value.9 true
    comment {
        access 'read write'
        type BOOLEAN
        count 10
    }
}
control.9 {
    iface MIXER
    name 'Mic Capture Switch'
    index 1
    value true
    comment {
        access 'read write'
        type BOOLEAN
        count 1
    }
}
control.10 {
    iface MIXER
    name 'Mic Capture Volume'
    value.0 255
    value.1 255
    value.2 255
    value.3 255
    value.4 255
    value.5 255
    value.6 255
    value.7 255
    value.8 255
    value.9 255
    comment {
        access 'read write'
        type INTEGER
        count 10
        range '0 - 255'
        dbmin -12750
        dbmax 0
        dbvalue.0 0
        dbvalue.1 0
        dbvalue.2 0
        dbvalue.3 0
        dbvalue.4 0
        dbvalue.5 0
        dbvalue.6 0
        dbvalue.7 0
        dbvalue.8 0
        dbvalue.9 0
    }
}
control.11 {
    iface MIXER
    name 'Mic Capture Volume'
    index 1
    value 255
    comment {
        access 'read write'
        type INTEGER
        count 1
        range '0 - 255'
        dbmin -12750
        dbmax 0
        dbvalue.0 0
    }
}

```

Is that playback channel map part of control.1 the key to setting up the signal routing?  I've tried everything I found remotely intuitive but I have not been able to get this device properly configured with ALSA.  I think part of the problem is it appears ALSA is thinking of the device as a surround-sound setup, rather than just a plain 2-speaker stereo system.  I do not know how to correct for that.  

Perhaps I need to create a new device and make a ttable to route the signals appropriately?  But what is that control.1 section for?  

Thanks for any help.  In case you are curious, my aplay -l output:

```
[COLOR=#111111][FONT=Consolas]**** List of PLAYBACK Hardware Devices ****[/FONT][/COLOR]card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]  
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USBStreamer [USBStreamer], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

update: If I convert the control.1 entry to this:

```

state.USBStreamer {control.1 {
    iface PCM
    name 'Playback Channel Map'
    value.0 0
    value.1 0
    value.2 0
    value.3 0
    value.4 0
    value.5 0
    value.6 0
    value.7 0
    value.8 3
    value.9 4
    comment {
        access read
        type INTEGER
        count 10
        range '0 - 36'
    }
}
```

then I can play direct to alsa:device=hw=1.0 via mplayer.   I missed this earlier because I must have mis-read the error message.   This USB audio device only accepts S32LE as its input format (yet strangely, it is a 24 bit LE audio device, but that's not how ALSA sees it).  

If I add -format s32le to the mplayer command-line, it will play files directly to the audio device.  Only they appear to be about twice as fast as they should be.  I suspect it's just converting the 16-bit data directly into 32-bit data, so it appears to be playing at double-time with a overlapping frequency-shift.  

So what I think I need to do to solve this problem is:

1) do a smarter conversion from 16-bit to 24-bit LE.  A little googling around and I find comments regarding LADSPA plugins. . . but I have not determined a way to get this done.

2) send the 24-bit LE to the usb device as 32-bit LE.  I suspect all I'll have to do it pad the 24-bit data with an extra byte of zeros. . . but who knows!

Potentially both these problems can be readily solved in one way.

---

### Post by delooper on 2016-07-10
Problem solved. 

> [COLOR=#000000][FONT=verdana]pcm.usbSTR {[/FONT][/COLOR][COLOR=#000000][FONT=verdana]  type hw
  card USBStreamer
  device 0
}[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]pcm.usbREMAP {
  type plug
  slave.pcm usbSTR
  ttable.0.8 1
  ttable.1.9 1
}[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]pcm.!default {
  type plug
  slave.pcm usbREMAP
}[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]ctl.!default {
  type plug
  slave.pcm usbREMAP
[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]}[/FONT][/COLOR]

Make the above into /etc/asound.conf

Ubuntu does not have this file, as ALSA is meant to be directly controlled by Pulse.  But this makes the usbstreamer the default ALSA device, and forces the proper channel mapping for usbstreamer to work correctly.   With this all the appropriate audio output format conversions appear to be taking place, although I'll look more closely into that in the future. 

Anyhow, problem appears to be solved.

---

