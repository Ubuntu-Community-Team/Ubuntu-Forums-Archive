---
title: "can't get jackd2 to work"
date: 2011-12-02
forum: Hardware
---

### Post by drjones on 2011-12-02
I am a newb linux user. I'm trying to get an alesis q25 midi controller to work in ubuntu 11.10. I followed some guides on the internet about using jack audio but cannot get it to work. the log screen for qjackctl says:
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]00:17:22.793 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]00:17:22.805 Statistics reset.[/COLOR]
 [COLOR=#cccc99]00:17:22.828 ALSA connection change.[/COLOR]
 [COLOR=#999999]00:17:22.970 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]00:17:22.977 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]00:18:10.604 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: driver "alsa" selected
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 00:17:45 2011: Starting jack server...
 Fri Dec  2 00:17:45 2011: JACK server starting in realtime mode with priority 10
 Fri Dec  2 00:17:45 2011: [1m[31mERROR: Cannot lock down memory area (Cannot allocate memory)[0m
 Fri Dec  2 00:17:45 2011: control device hw:0
 Fri Dec  2 00:17:45 2011: control device hw:0
 Fri Dec  2 00:17:45 2011: Acquired audio card Audio0
 Fri Dec  2 00:17:45 2011: creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 Fri Dec  2 00:17:45 2011: control device hw:0
 Fri Dec  2 00:17:45 2011: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 Fri Dec  2 00:17:45 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
 Fri Dec  2 00:17:45 2011: ALSA: use 3 periods for capture
 Fri Dec  2 00:17:45 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
 Fri Dec  2 00:17:45 2011: ALSA: use 3 periods for playback
 Fri Dec  2 00:17:45 2011: [1m[31mERROR: Cannot create thread res = 1[0m
 Fri Dec  2 00:17:45 2011: [1m[31mERROR: Cannot use real-time scheduling (RR/10)(1: Operation not permitted)[0m
 Fri Dec  2 00:17:45 2011: [1m[31mERROR: AcquireSelfRealTime error[0m
 Fri Dec  2 00:17:50 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Fri Dec  2 00:17:50 2011: [1m[31mERROR: Driver is not running[0m
 Fri Dec  2 00:17:50 2011: [1m[31mERROR: Cannot open client name = dbusapi[0m
 Fri Dec  2 00:17:50 2011: [1m[31mERROR: failed to create dbusapi jack client[0m
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#ff0000]00:18:22.699 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 Fri Dec  2 00:18:22 2011: [1m[31mERROR: JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Fri Dec  2 00:18:22 2011: [1m[31mERROR: Driver is not running[0m
 Fri Dec  2 00:18:22 2011: [1m[31mERROR: Cannot create new client[0m

```any help would be greatly appreciated! i can post additional data if needed, just tell me what commands i need to type i am super newb :)

edit: this is the info that i get from lspci for my soundcard:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASRock Incorporation Device 0397
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```i am not sure if it can do midi synth or not? i can play normal sound from web, mp3, movies ect.


edit: i downloaded a midi file to see if it would play on my system. when i opened it from firefox download window it launched banshee media player. banshee told me it needed some plugin to play it so i clicked ok. it automatically downloaded something (i didnt catch the name of what it installed). the midi file played in banshee after it installed the plugin it found. then i ran jack to see what happened and the jack server succesfully started this time! i can now launch apps that use jack audio, however i still cannot get any sound to play when i try to play the midi controller. i tried qsynth and zynaddsubfx but no sound comes out, i dont know if i have these programs set up properly or not to get playback. i will experiment more, please post some tips if anyone has some ideas for a struggling newb. :)
ouput for jack audio message log now says:
```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]14:21:40.692 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:21:40.700 Statistics reset.[/COLOR]
 [COLOR=#cccc99]14:21:40.709 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:21:40.730 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]14:21:48.168 D-BUS: JACK server is starting...[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]14:21:48.184 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: driver "alsa" selected
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Saving settings to "/home/drjones/.config/jack/conf.xml" ...
 Fri Dec  2 14:21:47 2011: Starting jack server...
 Fri Dec  2 14:21:47 2011: JACK server starting in non-realtime mode
 Fri Dec  2 14:21:48 2011: control device hw:0
 Fri Dec  2 14:21:48 2011: control device hw:0
 Fri Dec  2 14:21:48 2011: Acquired audio card Audio0
 Fri Dec  2 14:21:48 2011: creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
 Fri Dec  2 14:21:48 2011: control device hw:0
 Fri Dec  2 14:21:48 2011: configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
 Fri Dec  2 14:21:48 2011: ALSA: final selected sample format for capture: 32bit integer little-endian
 Fri Dec  2 14:21:48 2011: ALSA: use 2 periods for capture
 Fri Dec  2 14:21:48 2011: ALSA: final selected sample format for playback: 32bit integer little-endian
 Fri Dec  2 14:21:48 2011: ALSA: use 2 periods for playback
 Fri Dec  2 14:21:48 2011: scan: added port hw:1,0,0 in-hw-1-0-0-Q25-MIDI-1
 Fri Dec  2 14:21:48 2011: scan: added port hw:1,0,0 out-hw-1-0-0-Q25-MIDI-1
 Fri Dec  2 14:21:48 2011: scan: opened port hw:1,0,0 in-hw-1-0-0-Q25-MIDI-1
 Fri Dec  2 14:21:48 2011: scan: opened port hw:1,0,0 out-hw-1-0-0-Q25-MIDI-1
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:capture_1'
 Fri Dec  2 14:21:48 2011: New client 'system' with PID 0
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:capture_2'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_1'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_2'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_3'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_4'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_5'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_6'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_7'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:playback_8'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:midi_capture_1'
 Fri Dec  2 14:21:48 2011: graph reorder: new port 'system:midi_playback_1'
 Fri Dec  2 14:21:48 2011: New client 'PulseAudio JACK Sink' with PID 1584
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:rear-left' to 'system:playback_3'
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:rear-right' to 'system:playback_4'
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:front-center' to 'system:playback_5'
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:lfe' to 'system:playback_6'
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:side-left' to 'system:playback_7'
 Fri Dec  2 14:21:48 2011: Connecting 'PulseAudio JACK Sink:side-right' to 'system:playback_8'
 Fri Dec  2 14:21:48 2011: New client 'PulseAudio JACK Source' with PID 1584
 Fri Dec  2 14:21:48 2011: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
 Fri Dec  2 14:21:48 2011: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
 Fri Dec  2 14:21:48 2011: [1m[31mERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not run: state = 2[0m
 Fri Dec  2 14:21:48 2011: [1m[31mERROR: JackAudioDriver::ProcessGraphAsync: Process error[0m
 [COLOR=#9999cc]14:21:50.550 JACK connection change.[/COLOR]
 [COLOR=#999933]14:21:50.554 Server configuration saved to "/home/drjones/.jackdrc".[/COLOR]
 [COLOR=#999999]14:21:50.555 Statistics reset.[/COLOR]
 [COLOR=#999999]14:21:50.562 Client activated.[/COLOR]
 [COLOR=#cc9966]14:21:50.580 JACK connection graph change.[/COLOR]
 Fri Dec  2 14:21:50 2011: New client 'qjackctl' with PID 4933
```now i am thoroughly confused. i restarted my system and jack audio went back to not working. before restarting i had remove and reinstalled zynaddsubfx.

---

### Post by drjones on 2011-12-02
bump!

---

