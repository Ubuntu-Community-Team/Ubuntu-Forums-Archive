---
title: "M-Audio Firewire Solo"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by X-dark on 2007-07-25
Hello,
I use Ubuntu Studio.
I'm trying to use a M-Audio Firewire solo but I don't succeed.
I know I must use Freebob and Jack but when I try to launch freebob under Jack it doesn't work :
```
16:17:40.766 Patchbay deactivated.
16:17:40.806 Statistics reset.
16:17:40.830 MIDI connection graph change.
16:17:41.015 MIDI connection change.
16:17:42.759 Startup script...
16:17:42.759 artsshell -q terminate
can't create mcop directory
Creating link /home/cedric/.kde/socket-ubuntu.
16:17:42.990 Startup script terminated with exit status=256.
16:17:42.990 JACK is starting...
16:17:42.990 jackd-realtime -v -dfreebob -r44100 -p256 -n2 -i0 -o0
16:17:42.992 Could not start JACK. Sorry.
16:17:49.348 JACK was stopped successfully.
16:17:49.348 Post-shutdown script...
16:17:49.348 killall jackd
jackd: no process killed
16:17:49.566 Post-shutdown script terminated with exit status=256.
```

---

### Post by X-dark on 2007-07-27
UP


I'm sure someone can help me on this, please !!! This would really be appreciated.

---

### Post by iain_m on 2007-07-31
I asked about this in [this thread]("http://ubuntuforums.org/showthread.php?t=204584&page=3"). Still no luck for me with the FW Solo, I'm afraid. Has anyone got this working?

---

### Post by iain_m on 2007-08-02
I have had some success.

First check you have both Freebob and Jackd installed. Set System - preferences - sound to 'auto detect' for all options.

Then, what you need to do is go to /etc/udev/permissions.rules (this may have a slightly different name, e.g. with a number at the end)

Open the file and look for the line :
KERNEL=="raw1394",                              GROUP="disk"

Change GROUP="disk" to "audio" 

I think there is a way of then reloading these permissions without restarting, but I just restarted.

Having restarted I opened a terminal and typed jackd -d freebob

I then had sound!

HOWEVER I have no idea how to make this persist without needing to type jackd -d freebob each time.

Several (well-meaning!) people have tried to help by saying things like "you can use a firewire audio device with freebob and jackd" but I'm afraid that kind of explanation doesn't help me as a newbie!

---

### Post by X-dark on 2007-08-05
Thank you.

I've changed the permissions as you told me, except that it was for me in /etc/udev/rules.d/40-permissions.rules.
I've then restart Ubuntu. I've first tried to start jack with the GUI but this didn't work.
So I've used a terminal and jackd -d freebob.
What I've got is :

> jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.

But no more sound than before.
Note that I've a Realtek Audio Chip integrated in my notebook wich may cause a conflict. The sound work from there.

---

### Post by X-dark on 2007-08-05
If i type this *jackd -d freebob -d hw:1*
I got that :
> jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 1, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Invalid argument
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
Segmentation fault (core dumped)


---

### Post by X-dark on 2007-08-05
But the ieee1394 and raw1394 seem to be loaded because when I type this *dmesg | grep 1394*
I got :
> [    3.386000] ieee1394: Initialized config rom entry `ip1394'
[    4.443000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.705000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800036bcd1e]
[    5.709000] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000d6c0b001485f1]
[   17.638000] ieee1394: raw1394: /dev/raw1394 device initialized
[   17.645000] WARNING: The dv1394 driver is unsupported and will be removed from Linux soon. Use raw1394 instead.


---

### Post by iain_m on 2007-08-05
Hello X-dark, I'm sorry to hear it's still not working for you. The first terminal message you posted is the same as what I saw on my machine. At that point I opened one of the sample audio/video files and heard sound.

I don't know enough to know whether the integrated chip would be causing a conflict, sorry. Someone else may be able to help there.

Do you have the Jack Control Panel (install qjackctl - this will then be accessible via the Applications->Sound and Video menu)? 

Try different settings in the Jack Control Panel. Be sure first to choose the Freebob driver from the drop down box on the right of the control panel.

I had to increase the buffer size before getting smooth sound from the FW Solo.

Good luck! Let us know how you get on.

---

### Post by WestCoastSuccess on 2007-08-19
Hi X-Dark. I just bought the M-Audio FireWire Solo earlier today, and here's what I did to get it to work with JACK (was having the same problems you're having):
- change driver to freebob (obviously).
- change interface to hw:0.
- change input channels to 2.
- change output channels to 2.

Now try starting JACK and see if it starts OK. If it doesn't start but you get a message about "DRIVER NT: Could not start driver" you'll need to reset the bus. Download gscanbus [http://gscanbus.berlios.de](http://gscanbus.berlios.de). Once downloaded, just type gscanbus into a terminal to start it. It'll show graphically what's connected and you should see your FireWire Solo. Click "Control", then "Force Bus Reset". You might as well leave it open as once you get to fiddling with the settings to test latencies you'll get the same error after a few tries. Apparently the 1394 resources are not being freed properly.

On my AMD 64 X2 with 2GB RAM I"m getting stable 1.67ms latency with the following settings:

- realtime: checked
- priority: 76
- frames/period: 32
- sample rate: 96,000
- periods/buffer: 5

This is without the real-time kernel patch - haven't gotten around to installing that yet - I'm using low-latency kernel.

The formula for latency is frames per period X periods per buffer / sample rate (then divide by 1,000 to express it in ms).

Took me about 12 hours of research to figure all that out - best of luck!

---

### Post by WestCoastSuccess on 2007-08-19
PS: I'm using Feisty.

---

### Post by X-dark on 2007-08-19
Thank you. As soon I'll reboot to Ubuntu I'll try this.

---

### Post by X-dark on 2007-08-19
This is still not working. I've also tried with hw:1 "in case of". But in both cases I get this :

> 16:01:11.420 Startup script...
16:01:11.422 artsshell -q terminate
can't create mcop directory
Creating link /home/cedric/.kde/socket-ubuntu.
16:01:11.660 Startup script terminated with exit status=256.
16:01:11.661 JACK is starting...
16:01:11.662 jackd-realtime -v -dfreebob -dhw:0 -r44100 -p256 -n2 -i2 -o2
16:01:11.665 Could not start JACK. Sorry.
16:01:13.985 JACK was stopped successfully.
16:01:13.987 Post-shutdown script...
16:01:13.989 killall jackd
jackd: no process killed
16:01:14.209 Post-shutdown script terminated with exit status=256.

---

### Post by X-dark on 2007-08-19
OK I was using the jackd-realtime option.

So with the jackd option the server start. But there is still no sound.

In the connection window I see the 2 analog and the 2 spdif output. I can route the out of a software to them, but desperately no sound :(

---

### Post by X-dark on 2007-08-19
When I start it, I get that :

```
17:12:49.337 Patchbay deactivated.
17:12:49.339 Statistics reset.
17:12:49.373 MIDI connection graph change.
17:12:49.543 MIDI connection change.
17:13:14.603 Startup script...
17:13:14.603 artsshell -q terminate
can't create mcop directory
Creating link /home/cedric/.kde/socket-ubuntu.
17:13:14.830 Startup script terminated with exit status=256.
17:13:14.830 JACK is starting...
17:13:14.830 jackd -v -dfreebob -dhw:0 -r44100 -p32 -n5 -i2 -o2
17:13:14.832 JACK was started with PID=8741 (0x2225).
getting driver descriptor from /usr/lib/libjack0.100.0/jack_dummy.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_oss.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_freebob.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
required capabilities not available
capabilities: =
new client: freebob_pcm, id = 1 type 1 @ 0x806e4d0 fd = -1
Freebob using Firewire port 0, node -1
new buffer size 32
showDevice: not implemented
17:13:15.557 MIDI connection graph change.
FreeBoB MSG: Streaming thread running without Realtime scheduling
FreeBoB MSG: Registering capture port dev1c_SpdifIn L
FreeBoB MSG: Registering capture port dev1c_SpdifIn R
FreeBoB MSG: Registering capture port dev1c_LineIn L
FreeBoB MSG: Registering capture port dev1c_LineIn R
FreeBoB MSG: Registering playback port dev1p_SpdifOut L
FreeBoB MSG: Registering playback port dev1p_SpdifOut R
FreeBoB MSG: Registering playback port dev1p_LineOut L
FreeBoB MSG: Registering playback port dev1p_LineOut R
FreeBoB MSG: MIDI threads running without Realtime scheduling
FreeBoB MSG: MIDI queue thread started
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
registered port freebob_pcm:dev1c_SpdifIn L, offset = 128
registered port freebob_pcm:dev1c_SpdifIn R, offset = 256
registered port freebob_pcm:dev1c_LineIn L, offset = 384
registered port freebob_pcm:dev1c_LineIn R, offset = 512
registered port freebob_pcm:dev1p_SpdifOut L, offset = 0
registered port freebob_pcm:dev1p_SpdifOut R, offset = 0
registered port freebob_pcm:dev1p_LineOut L, offset = 0
registered port freebob_pcm:dev1p_LineOut R, offset = 0
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
8741 waiting for signals
17:13:17.019 Server configuration saved to "/home/cedric/.jackdrc".
17:13:17.020 Statistics reset.
17:13:17.023 Client activated.
17:13:17.024 Audio connection change.
17:13:17.025 Audio connection graph change.
new client: qjackctl-8723, id = 2 type 2 @ 0xb7f67000 fd = 15
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl-8723: start_fd=5, execution_order=0.
client qjackctl-8723: wait_fd=14, execution_order=1 (last client).
-- jack_rechain_graph()
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.0
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 44100
LibFreeBoB MSG:   Period Size              : 32
LibFreeBoB MSG:   Nb Buffers               : 5
FreeBoB MSG: xrun detected
17:13:17.047 XRUN callback (1).
LibFreeBoB MSG:   Directions               : 0
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 32 (0 / 128) (0 / 0 )
LibFreeBoB ERR: Xrun on connection 1
load = 20.2759 max usecs: 294.000, spare = 431.000
load = 13.5172 max usecs: 49.000, spare = 676.000
```

---

### Post by WestCoastSuccess on 2007-08-19
It looks to me like you just need to make the right connections and adjust some of the parameters to avoid the X Runs.

Looking at your settings, it should be showing a latency of 3.63ms. I'd get that higher until you have sound coming thru, then try lowering it. Try:

512 frames/buffer
96,000 sample rate
3 periods/buffer

That should give you a 16ms latency and be rock solid (ie no X Runs). Note that it's not uncommon to get an X Run when you start jack - don't worry about that one. 

Click "Setup" and then the "Display" tab and activate "Elapsed time since last X Run" - you can then see really easily if you're getting at least good stretches of time between X Runs.

Now for the connections. Here's what I did: I wasn't getting sound either at first, but I thought I'd try Ardour and see if any signal was making it thru. On opening Ardour, I got an error message that it can't connect to Alsa - I've attached a pic. Oh-oh, I thought, however I pushed on. If you expand Freebob in the Connections box in Jack, you should, in the left box,  see something like "dev1c_LineIn..." X 2 and "dev1c_SPDFlin..." also times 2.These correspond to the inputs on your FireWire Solo. In the right hand box, you should see, "dev1p_LIneOut..." twice and "dev1p_SPDIFOut..." twice - this corresponds with the output connections of the FireWire Solo. Once you create a session, Ardour should make the connection from Ardour to Freebob (meaning sound from Ardour will go thru the FireWire Solo), however in my case I had to manually make the connections from Freebob to Ardour to route the signal from the FireWire Solo into Ardour. I"ve attached a screenshot of my connections. The connections are: out from Ardour and into  the output of Freebob and also out from Freebob and into the inputs of Ardour.

At this point I had a guitar cable running from the guitar to the guitar input on the front of the FireWire Solo and just the firewire from the Solo to the computer. I added an audio track, hit record, and started playing the guitar. The sound waves started appearing in Ardour, so I knew the sound was making it thru, I just wasn't hearing it. Likewise on playback.

What I realized then was that I had assumed somewhat stupidly that the sound would output from the Solo thru the firewire cable and then be played by my computer (via the internal sound card, I guess) - I hadn't connected any speakers or audio equipment to the output connections of the Solo. I stuck a cable in the guitar plug output 1 on the back of the Solo, stuck an adapter to change it to a 1/8" plug on the other end and plugged it into the mic input on the front of my computer and hit play in Ardour - sound! That's obviously not the ideal way to set up the output, however it did confirm to me what I needed to do - hook up audio out connections to the back of the Solo unit.

Sorry, I'm a little punchy and just realized I'm rambling (it's not even noon and just awoke...) but I hope that makes some sense to you. Run a cable from the outputs on the back of the Solo either the input on some audio equipment or try an input on your computer (I'd suggest line rather than mic) if you want to route it thru your internal sound card, and see if that works.

Let me know if any of that solves the problem and sorry for the verbosity!

PS: In case it's not obvious, you need to hit the "start" button on jack as well as the play button (so that it shows "rolling").

PPS: you'll likely need to reset the bus with gscanbus first or jack may not start.

I'm amazed at how little documentation exists on any of this!

Now I need a very large coffee and a cigarette...

---

### Post by X-dark on 2007-08-19
Thank you

Ok I'll look to the X run issue.

But concerning the output, my FWSolo works well on windows Vista so everything is plugged fine.
Concerning patching in jack, I did it. I even tried to directly route the Analog Input (where my synth is plugged) to the analog output (where my stereo is plugged) but no sound.
I've tried with different software (XMMS, ZynAddSubFX, Ardour, ...) but no sound.

---

### Post by WestCoastSuccess on 2007-08-19
Have you tried recording with Ardour (or whatever) to see if the signal makes it thru?

One other thing, and I think it's a stretch, but I recall reading somewhere it's better to get power via the plug, rather than the firewire cable (but considering you got it running on windoze that's presumably a non-issue).

---

### Post by iain_m on 2007-08-21
Thanks WestCoastSuccess for the detailed account - glad to hear you got it working!

I'd managed to get sound out of it, but hadn't had a chance to really tweak it yet, so your guide will be useful when I do. :)

---

### Post by WestCoastSuccess on 2007-08-21
My pleasure - if it saves anyone the hours I spent tracking down the info I"ll be happy! When I get around to it I'll post comprehensive instructions - there really ought to be a place where the info to use this (and other) card(s) is all collected - the freebob site's supported applications page had me thrilled until I realized the links just point to the manufacturers' sites...no use at all in setting it all up. The connections in jack had me utterly confused until I spent 6 hours fooling around with them :)

There's good info on setting up real time here, btw:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

First few guitar bits recorded as a test and it sounds GREAT!

---

### Post by Denis69 on 2007-08-22
Hello, 
First, thanx for this thread, it was helpfull for me, and now, i know that's possible to make this card working on my Ubuntu...
I've a ubuntu Studio 7.04 and the same audio card : M-Audio Firewire Solo...
It does not work, i've this error with QJackCtrl :
Could not connect to jack server as client...

here is the log :

16:14:45.946 Startup script terminated with exit status=256.
16:14:45.949 JACK is starting...
16:14:45.951 jackd -v -m -dfreebob -dhw:0 -r44100 -p32 -n5 -i2 -o2
16:14:45.974 JACK was started with PID=12800 (0x3200).
getting driver descriptor from /usr/local/lib/jack/jack_dummy.so
getting driver descriptor from /usr/local/lib/jack/jack_alsa.so
getting driver descriptor from /usr/local/lib/jack/jack_oss.so
getting driver descriptor from /usr/local/lib/jack/jack_freebob.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
Freebob using Firewire port 0, node -1
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: freebob_pcm, id = 1 type 1 @ 0x806eb80 fd = -1
new buffer size 32
showDevice: not implemented
16:14:47.396 MIDI connection graph change.
FreeBoB MSG: Streaming thread running without Realtime scheduling
FreeBoB MSG: Registering capture port dev1c_LineIn 1+2 left
FreeBoB MSG: Registering capture port dev1c_LineIn 1+2 right
FreeBoB MSG: Registering capture port dev1c_SpdifIn 1+2 left
FreeBoB MSG: Registering capture port dev1c_SpdifIn 1+2 right
FreeBoB MSG: Registering playback port dev1p_LineOut 1+2 left
FreeBoB MSG: Registering playback port dev1p_LineOut 1+2 right
FreeBoB MSG: Registering playback port dev1p_SpdifOut 1+2 left
FreeBoB MSG: Registering playback port dev1p_SpdifOut 1+2 right
FreeBoB MSG: MIDI threads running without Realtime scheduling
FreeBoB MSG: MIDI queue thread started
registered port freebob_pcm:dev1c_LineIn 1+2 left, offset = 128
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
registered port freebob_pcm:dev1c_LineIn 1+2 right, offset = 256
registered port freebob_pcm:dev1c_SpdifIn 1+2 left, offset = 384
registered port freebob_pcm:dev1c_SpdifIn 1+2 right, offset = 512
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
12800 waiting for signals
registered port freebob_pcm:dev1p_LineOut 1+2 left, offset = 0
registered port freebob_pcm:dev1p_LineOut 1+2 right, offset = 0
registered port freebob_pcm:dev1p_SpdifOut 1+2 left, offset = 0
registered port freebob_pcm:dev1p_SpdifOut 1+2 right, offset = 0
++ jack_rechain_graph(): client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
16:14:48.074 Could not connect to JACK server as client. Please check the messages window for more info.::

Any ideas ?
Thanx

---

### Post by WestCoastSuccess on 2007-08-23
It looks to me like it's connecting OK to jack but overwhelming jack - can you post your settings (suggested settings for the purposes of setup in brackets - you'll want to adjust some of these later to better your latency but you want a bigger latency to get the connection established):

-frames/period (512)
-sample rate (48,000)
-periods/buffer (3)
-input channels (2)
-output channels (2)
-interface (hw:0)
-latency (should show 32 ms with these settings)

---

### Post by Denis69 on 2007-08-30
Thanks,
I 've tried this setting (and more...) but in fact i've just changed the server path, the right path is /usr/bin/jackd 
For this moment, the sound is not OK but I haven't time to check because I go away on holidays. I'll test it the next week. Thanx for the help

---

### Post by zbyszek_zbl on 2007-10-27
Hi. Any additional news about Firewire Solo? I've tried everything from this tread (firstly on 7.04 and now on 7.10) and in Ardour I see that I have sound in, but I can't get sound out! I can record something with ardour and then play it through alsa and my internal card, but I have no sound from my firewire solo. Device is OK because I use it with my iBook with MacOS X 10.4.10 and it works without problems. I've tried everything in jackd connection settings, I/ve tried to change latency and buffers, I even tried to change kernel to lowlatency and realtime - still no sound out :-( and I really have no more ideas what else I could try...

---

### Post by zbyszek_zbl on 2007-10-27
Additional info... In nearly all post connected with fire wire solo I can see that people have this device in "Device manager". I have not... It is not listed at all and "gscanbus" tells only about : ?S400 Unknown. Firewire solo is the only one firewire device in my system. I have all necesary changes i udev permission rules and I have raw1394 module loaded at system startup... May be here is the problem...

---

### Post by WestCoastSuccess on 2007-11-07
If you can get sound into Ardour and hear it upon playback, your problem is in the monitoring. Can you run qjackctl and Ardour, open the connections box, expand everything and post a screen shot? On mine, I run a cable from the balanced output in the rear of the Firewire Solo into the input of my onboard sound card. Once you've done that, couple of things to check:

- open alsamixer and check if any of the outputs are muted or have their volume down to 0.
- plug headphones into the Firewire Solo - do you hear anything when recording in Ardour?
- in the qjackctl connection box, set up a connection between freebob on the left and freebob on the right. The connections you want on the right depend on what your using to output to your sound card (or stereo or speakers or whatever). Use the top 2 unless you're using spdif, in which case use the bottom 2.
- check your monitoring connections in Ardour: when you set up a session, click the advanced button to show additional options, and have it set up a master bus and a monitor bus. Connect the track outputs from Ardour in the left side of the connections panel to the monitor inputs on the right side, then connect the left side monitor outputs to the freebob inputs on the right side.
- there are hardware and software monitoring options in Ardour, tho I can't at the moment recall how mine's set up - try checking out the forums at the Ardour site.

Good luck - let me know how it turns out!

---

### Post by zbyszek_zbl on 2007-11-10
In Ardour I can see that I have sound in but I can't hear anything. When I plug the headphones into the FireWire Solo I don't have any sound. My FireWire Solo works normally with my iBook (MacOS X) so cable connections are OK. I think that in jackctl connections are OK too - I've checked it with my friend comuter. I've taken my FireWire Solo to him and set up everything the same way as on my comp and the sound was OK... After connecting FireWire Solo I have in dmesg something like this:
[ 2585.955971] ieee1394: Error parsing configrom for node 0-00:1023
[ 2585.956037] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 2587.794750] doh, someone wants to mess with state set
Hardware problem or I have something wrong with my system? I really have no ideas...

---

### Post by WestCoastSuccess on 2007-11-10
This is a shot in the dark, however it seems to me the problem lies in your firewire driver - here's some code that includes the error message your getting:

[http://metacomp.stanford.edu/linux/oses/linux/2.3.50/drivers/ieee1394/csr.c](http://metacomp.stanford.edu/linux/oses/linux/2.3.50/drivers/ieee1394/csr.c)

Assume you have libiec61883 and libraw1394 installed? Do you have any other firewire devices connected?

---

### Post by zbyszek_zbl on 2007-11-10
Yes I Have libiec and libraw and I have correct permissions to libraw... I have two harddisk in firewire cases and they work OK. I will try to download and compile the newest ieee1394 drivers

---

### Post by X-dark on 2007-11-12
Yeahhhhhh!!!!!!!!!

It works.

I've just made a fresh install of Ubuntu 7.10 64 bits. Then I've installed the realtime kernel. Then I've changed the perms for raw1394. And then I've typed jackd -d freebob in a terminal.
Now I can play audio file in Audacious.

---

### Post by zbyszek_zbl on 2007-11-12
I think I'll give up... Fresh ieee1394 drivers compiled from source - no change... Another firewire card (old was on Via chipset, now I have Nec chipset) - no change... My computer is Dell GX260. It has only two PCI slots. In the first there is firewire card, and in the second TV tuner. I,ve tried to change the order of the cards - no change. May be something is wrong with IRQ's, but I don't know how to check it. It looks like a strange hardware problem... To be sure in next days I will try to install it with my firewire card on my friend's Ubuntu...

---

### Post by codion on 2007-11-15
It's very useful~
I'm a firewire solo user in China,and i am try to find out how could it be work for so long times,
I'll try this ,wish it be OK~
Thank you~

---

### Post by X-dark on 2007-11-15
> **X-dark said:**
> Yeahhhhhh!!!!!!!!!

It works.

I've just made a fresh install of Ubuntu 7.10 64 bits. Then I've installed the realtime kernel. Then I've changed the perms for raw1394. And then I've typed jackd -d freebob in a terminal.
Now I can play audio file in Audacious.

Today I haven't been able to make it works again. I'll try again.

---

### Post by WestCoastSuccess on 2007-11-19
X-Dark: what errors are you getting? Lots of X-Runs or just doesn't start? If it won't start, try downloading gscanbus and follow my directions from a prior port. I'm running exactly the same setup - Ubuntu Gutsy (7.10) with real time kernel on x64. Mine runs for days at 2ms with no Xruns whatsoever, so it IS possible.

Zbyszak: any luck on your friend's Ubuntu?  If not, what error messages are you getting?

---

### Post by zbyszek_zbl on 2007-11-20
Hi. I've managed to run FireWire Solo on my friend's ubuntu, but there is something strange ;-). First we had to boot into Windows and enable firewire solo under windows. After that Ubuntu started to see firewire solo in hardware manager and it started to work. Earlier I used my FW Solo with MacOS X and during first start mac driver updated firmware. After that it was working without problems with Mac, but no with Linux. Enabling it under Windows was in fact loading another firmware by Windows driver and it looks like Ubuntu works olny with tis windows version.
About my computers - Dell GX 260 still doesn't work with fw solo, and after connecting fw to it I had to run it under Windows again to have sound out on another computer (looks like Dell mess with internal mixer of FW Solo or something like this). But now I 've managed to run FW Solo on Acer TM 7520 with 64bit Gutsy and I have sound in and out :-). In next few days I will try realtime kernel on both computers - may be it will be a solution for Dell and I'm sure it will be good idea for Acer because with "standard" kernel I have latency about 16 - with less I have a lot of X-Runs and FW Solo stops working.

---

### Post by X-dark on 2007-11-20
> **WestCoastSuccess said:**
> X-Dark: what errors are you getting? Lots of X-Runs or just doesn't start? If it won't start, try downloading gscanbus and follow my directions from a prior port. I'm running exactly the same setup - Ubuntu Gutsy (7.10) with real time kernel on x64. Mine runs for days at 2ms with no Xruns whatsoever, so it IS possible.


No errors, no X-Runs. It's just I can't hear any sound. The output are correctly mapped, I didn't change anything since last time but desperatly no sound.

---

### Post by WestCoastSuccess on 2007-11-21
X-dark: Do you have a cable running out of the Firewire Solo and into a line input for your onboard soundcard?

zbyszek_zbl: can you post your setting for jack? You ought to be able to get better latency without a realtime kernal than 16ms - I was getting 4ms without rt w/dual core amd 64 & 2GB ram.

---

### Post by zbyszek_zbl on 2007-11-25
OK - doesn/t matter with latency for now... I have bigger problem. It seems that my previous post were to fast :-/. My firewire solo works well on every computer with Ubuntu but only just after enabling it on Windows. If I have firewire solo connected to Ubuntu, and than I switch of the computer, after switch it on again I have no sound out. I must connect it for a while to Windows computer with firewire solo drivers (only connect - nothing more...), and than I can disconnect it and connect to another computer with Ubuntu or restart this one into Ubuntu and I have full working firewire solo. Unfortunatelly only till the next system restart... Any ideas?

---

### Post by WestCoastSuccess on 2007-11-25
Can you be more specific? Does sound make it through any stage: if you have a sound source hooked up to input 2 and crank up the gain, does the clip light come on? Do the freebob drivers show up in qjackctl? If you start Ardour and setup an audio track to record, does it show input on the level meters on the mixer strip?

Does it help if you force a bus reset via gscanbus? 

Can you post the output of lsmod? When you have it hooked up to ubuntu but it's not working, does plugreport show that firewire solo is being recognized?

Shot in the dark here, but do you keep the Firewire Solo plugged in to a wall socket? Mine's plugged in 24/7 so it never loses power between the odd reboot (actually my computer stays on 24/7 too but gets rebooted perhaps once every month or so). Try getting it going with windoze, keeping it plugged into the wall while you switch it to ubuntu and see if that works.

Just some blind guesses but it'll help us narrow down the problem...

---

### Post by zbyszek_zbl on 2007-11-25
>>Shot in the dark here, but do you keep the Firewire Solo plugged in to a wall socket?

Perfect :-). It was the clue. One of my computers is laptop with 4 pin firewire so I had to use AC power. The second is Dell GX260 with normal 6 pin firewire so after connecting m-audio to it I disconnected AC power and fire wire solo was working only till the next reboot. Now I left AC power on, rebooted computer several times to be sure and it still works :-) 
It looks like in my firewire solo output ports are muted when it is disconnected from AC power. On OSX and Windows there is mixer program for it and after connect it automaticly goes back to previously difined state. Unfotunaltelly in Ubuntu there is no such aplication so there is no sound out. AC power connected all the time seems to be the best and only solution for now. May be the next versions of jakcd and freebob will have some kind of mixer :-)
Thanks a lot - this thread is the best tutorial how to make firewire solo working with linux in all the web :-)

---

### Post by X-dark on 2007-11-25
> **WestCoastSuccess said:**
> X-dark: Do you have a cable running out of the Firewire Solo and into a line input for your onboard soundcard?
No
The analog output are connected to my speakers.

---

### Post by WestCoastSuccess on 2007-11-25
X-Dark: Try running a line from the balanced output of the firewire solo to a line input on your computer. Make sure the line is not muted (use alsamixer and just un-mute everything and turn all the levels to full). See also zbyszek's issues in this thread.

zbyszek: Glad to hear the power plug idea worked! if you don't have it installed already, install alsamixer - it's a graphical mixer app and you'll be able to see which inputs/outputs are muted and adjust volumes, etc. As an experiment, try unplugging the unit and rebooting and see if any of the settings in alsamixer change (do a screenshot before and after).

---

### Post by X-dark on 2007-11-25
> **WestCoastSuccess said:**
> X-Dark: Try running a line from the balanced output of the firewire solo to a line input on your computer. Make sure the line is not muted (use alsamixer and just un-mute everything and turn all the levels to full). See also zbyszek's issues in this thread.

I'm sorry but I don't see the point. There is no sound neither in my speakers neither if a plug a headset in the dedicated output.
I'll investigate further zbyszek's issues in this thread.

---

### Post by WestCoastSuccess on 2007-11-25
Here's a screenshot of alsamixer...

PS: setting shown are settings I use for recording via Ardour using firewire solo.

---

### Post by WestCoastSuccess on 2007-11-25
If you're not hearing anything in the headphone output on the firewire solo unit itself, then you do have a problem. What do you have hooked up to the firewire solo input? If you have a guitar or keyboard handy, plug its output into input 2 on the front of the firewire solo. Make sure the gain is turned up - turn it all the way up and see if the clip light comes on to confirm the signal is at least making it into the firewire solo. Plug headphones into firewire output, then turn the level dial up and play the instrument (just hold the headphones close to your ears at first - it could be damagingly loud if the input gain is cranked way up) - any output in the headphones?

If not, try another cable between the instrument and the firewire solo.

Let me know either way - it'll help narrow things down.

PS: reason I suggested connecting to your sound card is that going directly from the firewire solo to the speakers I believe leaves the sound unamplified (unless you have active speakers). For example, my signal runs out from my firewire solo's balanced output and into a line input of my computer and then out from my computer into an amplifier and out from there to the speakers (altho I could also just go directly from the firewire solo into the amplifier)...

PPS: In alsamixer, make sure there's a checkmark in the Headphones box under the Switches tab (see screenshot attached).

---

### Post by zbyszek_zbl on 2007-11-25
X-dark: I think you have similar problem to mine. I had everything set OK, all cables pluged well and checket twice to be sure and I had no sound out on any firewire solo output. I had sound in but not uot - try ardour. It has mixer and you can see if you have sound in on mixer strip. You can try to record something and than try to play it through alsa. For me it worked, I only hadn't sound out from firewire solo. And (THANKS WestCoastSuccess :-D) I just had to enable firewire solo under Windows and that remember about keep it on AC Power and it works.
WestCoastSuccess: I have alsamixer, but it shows only alsa outputs so it isn't possible to check what is state of freebob outputs. For now the only way for me is keep firewire on AC Power and wait for application like freebobmixer or something like this :-)

---

### Post by X-dark on 2007-11-25
I'm sure there is no problem in my cable or my connections. I use my firewire solo for a long time in Windows and it works perfectly.
I use the AC power since I have a laptop.
I'll try to use it under Windows then reboot to Ubuntu to see if it helps.
I'll also try to see if I can record something.

---

### Post by WestCoastSuccess on 2007-11-25
zbyszek: your comments about alsamixer are quite correct, except if the problem is that the signal is making it thru to, say Ardour (as you've suggested) but not to your speakers and you're re-routing it thru your onboard sound card (as I am)...

The thing for X-Dark to do is take it one segment at a time to find out where exactly the problem lies - X-Dark: I'm sure you've already tested each of these steps, in order, however I write these down in detail for the next person who tries to set up a firewire solo and doesn't necessarily have your experience with Ardour and qjackctl:

1) is the signal making it into firewire? Test using clip light on firewire solo as previously explained. If light never comes on even at full gain and full volume of instrument, try another cable. Still no light? Possibly a dud unit (tho I've yet to hear of one...).

2) is the signal making it out of the firewire solo and into your computer? Test using Ardour as zbyszek suggests - if you get a level on the mixer's level meter you know your firewire solo is outputting your signal.

To clarify: plug a guitar or keyboard or bass or whatever into input 2 of the firewire solo. Start qjackctl (see example settings for qjackctl in screenshot below - if that doesn't work/gives you too many Xruns, change frames/period to 512 and try again), then start Ardour. Set up a new track in Ardour. Click Connections and confirm there's a connection from freebob on the left to Ardour on the right. You'll want to expand the freebob connection on the left and the Ardour connection on the right. Check that the 2nd input from the top of freebob (on mine it's called "devlc_LineIn 1+2 right" - this corresponds to input 2 (the one for the guitar cable) on the front of the firewire solo) is connected to Audio1 under Ardour on the right of the Connections box (**note that Ardour/jack tend to default connections to spdif (at least on my setup) even when spdif connections are not physically being used, so make sure you don't skip this step)**. If it isn't, making connections in qjackctl is easy: click the particular output you want on the left, click the particular input you want on the right, then click the Connect button. Then connect the Audio 1 outputs from the left side of the Connections box (under Ardour) to the "devlp_LineOut 1+2 right" and "devlp_LineOut 1+2 left" under freebob on the right side of the Connections box (if you're using the balanced outputs on the back of the firewire solo) or devlp_Spdif 1+2 right and devlp_Spdif 1+2 left (if your outputting via spdif cables from back of the solo unit). See 2nd screenshot below for an example of how the connections should look for the purposes of testing.

In Ardour, arm for recording the track you added. This involves clicking the the red "O" near the left of Ardour, then clicking the Record button at the top near the transport buttons (it will start flashing). See 3rd screenshot below. Don't worry, it won't start recording until you also click the Play button, but it will allow you to check if the signal is getting thru. Click the Options tab in Ardour, hover over Monitoring and make sure there's a little dot next to Software Monitoring. Click the Windows tab and then click Show Mixer. Strum your guitar/strike your keyboard keys/whatever and watch those level meters in the mixer strip - do they light up and indicate a signal? Great - move on to step 3. If they don't show any signal, unplug the power plug from your firewire solo; turn off your computer. Plug the power plug back in & reboot the computer and try again. If qjackctl fails to start, run gscanbus and force a bus reset. If that doesn't work, post here for help.

3) that only leaves the signal from the computer back out as the culprit. Solution here depends on how your output to speakers is set up. Obviously your output from Ardour should go to the freebob input in qjackctl - that sends the signal back to the firewire solo. Once that's confirmed, check the headphone output on the solo unit. If you're getting levels in the mixer of Ardour but no sound at headphone jack on solo, likely problem is connections in qjackctl. If you are getting sound, problem lies in the connection from the output(s) on the back of the solo unit to the input of whatever you're using to listen to the sound. Test by running a cable from balanced output on solo to line input on onboard soundcard and see if you get sound. If you do, problem is in how you have the output of solo connected to your speakers/amplifier/computer/receiver. If you don't, check alsamixer to make sure the input for the onboard sound card is not muted or volume turned way down. Still not working? Try another output from solo. Still not working? Try original output from solo and another line input on the onboard sound card. If that fails, try a different cable between solo rear output and onboard sound card input.

If that doesn't work, post here, including which of the above steps worked...

---

### Post by X-dark on 2007-11-26
First point, I can't activate realtime. I get this error :
```
cannot use real-time scheduling (FIFO at priority 10) [for thread -726700624, from thread -726700624] (1: Operation not permitted)
```

(I'm running the rt kernel.)

---

### Post by X-dark on 2007-11-26
I've tried to run qjackqtl with sudo and the same settings. I get this log :
```
10:19:14.820 Patchbay deactivated.
10:19:14.825 Statistics reset.
JACK tmpdir identified as [/dev/shm]
10:19:14.848 MIDI connection graph change.
10:19:15.031 MIDI connection change.
10:20:19.754 Patchbay deactivated.
10:20:23.605 Startup script...
10:20:23.606 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /root/.kde/socket-cedric-laptop.
10:20:23.841 Startup script terminated with exit status=256.
10:20:23.842 JACK is starting...
10:20:23.843 /usr/bin/jackd -R -P89 -p128 -t1000 -dfreebob -dhw:0 -r96000 -p64 -n3 -D
10:20:23.849 JACK was started with PID=6592 (0x19c0).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
Freebob using Firewire port 0, node -1
10:20:24.642 MIDI connection graph change.
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
10:20:25.905 Server configuration saved to "/root/.jackdrc".
10:20:25.909 Statistics reset.
10:20:26.186 Client activated.
10:20:26.193 Audio connection change.
10:20:26.199 Audio connection graph change.
JACK tmpdir identified as [/dev/shm]
SSE2 detected
10:20:30.930 MIDI connection graph change.
zombified - calling shutdown handler
10:20:30.932 Shutdown notification.
10:20:30.933 Client deactivated.
10:20:30.934 JACK was stopped successfully.
10:20:30.935 Post-shutdown script...
10:20:30.935 killall jackd
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
jackd: no process killed
10:20:31.157 Post-shutdown script terminated with exit status=256.
```

---

### Post by WestCoastSuccess on 2007-11-26
Don't worry about any of the error messages appearing above

"zombified - calling shutdown handler"

I get those too and they can be ignored.

Try unchecking the real time box in qjackctl setup and see if that gets jack running - we'll worry about rt once you're getting sound out of your speakers...

You might also want to change the frames/period to 512 while you're getting firewire solo working.

---

### Post by WestCoastSuccess on 2007-11-26
You may need to reboot to kill the zombified jack process.

After than, you can also try:

#cat /proc/interrupts

That'll show you your IRQ numbers - here's what mine outputs:

$ cat /proc/interrupts
           CPU0       CPU1       
  0:        401        511   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          0          0   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          0          4   IO-APIC-edge      i8042
 14:      17298    2699199   IO-APIC-edge      ide0
 16:     443353   52682602   IO-APIC-fasteoi   sata_sil24, ohci1394, nvidia
 17:      77150   13619147   IO-APIC-fasteoi   ivtv0
 20:      16028    2173397   IO-APIC-fasteoi   sata_nv, HDA Intel
 21:        148      12560   IO-APIC-fasteoi   ehci_hcd:usb1, sata_nv
 22:      71388    9021611   IO-APIC-fasteoi   sata_nv, eth1
 23:      77729    9586719   IO-APIC-fasteoi   ohci_hcd:usb2, eth0
NMI:          0          0 
LOC:  168310509  183863886 
ERR:          0


The 2 important ones in my case are 8 (rtc = real time clock) and 16 (ohci1394 = firewire).

You can change the priorities for these via:

#sudo chrt -f -p 98 `pidof "IRQ-8"`
#sudo chrt -f -p 82 `pidof "IRQ-16"`

Be sure to insert your applicable IRQ numbers. Also note the uptick at the end of the line - it's NOT a quotation mark - rather it's the key above the tab key - same key as "~".

You can then try starting qjackctl again, then type

#top

in a console. Jack and firewire should stay at the top of the display - here's a snapshot of mine - jackd  and IRQ16 NEVER move from the top of the list:

$ top

top - 08:55:54 up 1 day, 36 min,  2 users,  load average: 0.40, 0.37, 0.31
Tasks: 182 total,   1 running, 181 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.9%us,  5.8%sy,  0.0%ni, 80.8%id,  0.0%wa,  0.2%hi,  0.3%si,  0.0%st
Mem:   4011640k total,  3245932k used,   765708k free,    81048k buffers
Swap:  8980304k total,    38816k used,  8941488k free,  2369000k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
18265 martin    20   0 84040  52m 9516 S   14  1.3   0:08.52 jackd              
 2554 root     -51  -5     0    0    0 S    6  0.0  27:22.19 IRQ-16             
16066 root      20   0  181m  53m 9.9m S    4  1.4   2:01.68 Xorg               
18256 martin    20   0  105m  26m  22m S    3  0.7   0:02.51 qjackctl           
16250 martin    20   0  278m  88m  18m S    2  2.3   4:03.75 compiz.real        
18279 martin    20   0  684m 114m  64m S    2  2.9   0:01.89 ardour-2.0.5       
16324 martin    20   0  180m 9716 7760 S    1  0.2   1:58.20 multiload-apple    
    6 root     -51  -5     0    0    0 S    0  0.0   2:41.56 softirq-timer/0    
   19 root     -51  -5     0    0    0 S    0  0.0   1:39.96 softirq-timer/1    
   24 root     -51  -5     0    0    0 S    0  0.0   0:05.87 softirq-sched/1    
16286 martin    20   0  403m  16m 9996 S    0  0.4   0:17.17 mythbackend        
18322 martin    20   0 19080 1384  972 R    0  0.0   0:00.11 top                
    1 root      20   0  5116 1968  572 S    0  0.0   0:00.79 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-high/0

---

### Post by zbyszek_zbl on 2007-11-26
> **X-dark said:**
> First point, I can't activate realtime. I get this error :
```
cannot use real-time scheduling (FIFO at priority 10) [for thread -726700624, from thread -726700624] (1: Operation not permitted)
```

(I'm running the rt kernel.)

About real time - I had the same problem and  to activatereal time I had to add three following lines to file /etc/security/limits.conf :
@audio	        -       rtprio  99
@audio          -       memlock 860000
@audio          -       nice    -10

---

### Post by X-dark on 2007-11-26
I've desactivated RT and switched to 512 samples. I can see level in the input of Ardour. So the problem is the output.

---

### Post by WestCoastSuccess on 2007-11-26
That's great - progress is being made!

Now presuming you have the track which displays levels in Ardour connected to freebob on the right side of the Connections box in qjackctl, try the headphones on the firewire solo - any sound?

---

### Post by X-dark on 2007-11-27
No, no still no sound. That's the point. The connection seems ok but there is no sound coming out.
I have to try to power it under Windows then reboot under Ubuntu without unplugging it.

---

### Post by WestCoastSuccess on 2007-11-27
Just so you're aware, X-Dark, windoze had nothing to do with it - the issue was keeping the power plug plugged in - it was incidental that zbyszek's windoze machine had only a 4 pin firewire connection, which meant he HAD to plug it in on the windoze machine, whereas his ubuntu machine had the 6 pin firewire plug, which led him to believe he didn't need to plug in to the wall socket. Just leave it plugged in and reboot.

Just so we're on the same page at this point, you've confirmed there's a dot next to "Software Monitoring" in Ardour, and you've tested the headphone jack on the firewire solo and found there to be no sound?

---

### Post by X-dark on 2007-11-27
Ok I quickly read it and I didn't really understand the thing with the AC.
So it's plugged : everything sould be fine.
I confirm I have software monitoring activated and no sound through the headphone.
I have also no sound when I directly plug the input to the output or when I play a MP3 with audacious and the Jack output activated.

The weirdest thing is the fact I achieved to have sound several days ago but since then nothing.

---

### Post by WestCoastSuccess on 2007-12-03
Can you post a screenshot of your qjackctl connections?

Also of your qjackctl setup screen?

---

### Post by X-dark on 2007-12-14
Here is a screenshot of my setup and connections. It's with Audacious.

---

### Post by X-dark on 2007-12-14
And here with Ardour

---

### Post by zbyszek_zbl on 2007-12-14
X-dark - about AC. The point in my case is that my M-audio internal mixer mute all outputs when it is unpowered. Windows drivers automaticly turn audio autputs in M-audio on, but if i unplug my AC adapter audio outputs are off again and Ubuntu drivers can't "unmute" them. So in my case the point is:
1. plug AC power to M-audio
2. Boot into Windows and activate M-audio
3. all the time keep m-audio powered by AC
4. boot into Ubuntu and use m-audio

Every time I remove AC adapter from m-audio and live it unpowered for a while I have to power it again, boot into windows, and than keep it powered till I boot into Ubuntu.

Wow - my English is bad but i hope now it is easier to understand what is the problem with AC power in my case.

---

### Post by X-dark on 2007-12-14
This is the way I understood it before. So I've definitively to try that.

---

### Post by WestCoastSuccess on 2007-12-15
Couple of things I notice from your screenshots:

1) In the Ardour example, disconnect Audio 1/Out 1 from dev_1p_Line_Out_L and connect Audio1/Out 1 to dev_1p_Line_Out_R. That should get you hearing output. It looks like you have a signal panned right going into Audio 1 but which then feeds to an output panned left.

2) The way you have your connections set up in Ardour is not correct. The Master Outs need something going IN to them.The normal way I'd set those connections up is:

- Connect dev1c_LineIn_R to both Audio 1/In 1 AND Audio 1/in 2 (since you've created a stereo track).
- Then, on the left side, connect Audio 1/Out 1 to master/In 1 and connect
Audio 1/Out 2 to master/in 2 on the right side.
- Then connect master/out 1 on the left to dev_1p_LineOut_L on the right and master/out2 to dev_1p_LineOut_R

See screenshot for example.

Try hitting Disconnect All and setting it up as I've described above and that should work. But try step 1 first!

---

### Post by ghostandmachine on 2008-01-13
Sorry to bring back an old post, but could someone be kind enough to write a simple tut in setting up the Firewire Solo in Ubuntu. Thanks in advance.

---

### Post by WestCoastSuccess on 2008-01-13
Been meaning to do just that but haven't had time (and won't in the near future - will be on the road for the next month).

Will try to get around to it late Feb. In the meantime, post #9 more or less contains everything you need, and if you have problems scroll thru the other posts and if that doesn't solve it, post here...

---

### Post by pedrogent on 2008-03-01
Well, it's back to Windows for me unfortunately.

This is complete insanity to just get sounds playing thru' speakers.

Best of luck everyone.

---

### Post by J$oney on 2008-03-01
What i would do if you are still having problems, is run Virtual Box with Xp as guest, get it running since the drivers that you get with the m-audio box will work. Use it like this till you figure it out on unbuntu. That's what i'm doing with everything, I just switched to ubuntu, and i'll be trying to configure a firepod, audition, and alot of midi controllers, and synth programs soon enough. But i don't like down time so while I configure atleast i have them running in windows, but trust me i'm trying to get away far away from microsoft, they've irritated me to much to use them anymore.

---

### Post by WestCoastSuccess on 2008-03-01
Sorry to hear of your frustrations, pedrogent.

Can you describe where exactly the problem is? By that, I mean, if you connect a guitar to the FireWire Solo, run qjackctl and start Ardour and try recording a track, do the level meters on the mixer indicate activity? Does the track actually record sound (you can tell by the wave depictions)? This is important in isolating where the problem lies.

Also, check the input selector on the front (button on the left, immediately to the left of the "Input 2" plug) of the FireWire Solo and make sure it matches your input - if you're recording a guitar, the guitar ought to plug into the front input jack, and the input selector ought to be out (ie "front" should be selected).

Once you've done that, report back and we can continue to narrow down the trouble spot until we've got you up and running.

Don't give up yet: once you get this running you'll really appreciate the sound quality and the low latency.


Cheers!

---

### Post by pedrogent on 2008-03-01
Hi folks.

Thanks very much for your replies. But the fact is I've been mucking around with Linux for a few years now and I (personally) feel it's not ready for people like me just yet... perhaps in a few years.

What people like me want is to be able to plug something in and for it then to work. We don't want to teach ourselves a computer science course to get something installed and working.

I appreciate that Linux has come a long long way in this regard but it's still a long road ahead.

Look: I want to use Linux. I like the idea. In fact, I use it on two of my computers at home already. But when it comes to anything not 'standard - e.g. a firewire soundcard' it takes one hell of a muck around to get things to work. This will push people away.

Good luck everyone. I write this to you from XP x64.

---

### Post by WestCoastSuccess on 2008-03-02
Lol - you give up pretty easily - I switched to Ubuntu less than a year ago and it's FAR easier than anything ms produces. Of course, on the odd occasion I've needed help, I posted details of my issue and received help promptly from a wide variety of people, on their own time. It's also been much faster and less frustrating than any IT help center I've ever phoned...

I can't see where you've posted at which point you're having problems - did you try my suggestions in the prior post? I'm more than happy to help - just take a moment and describe how far you got.

1. Do you have Ardour installed? I presume you have a FireWire Solo in order to record music, and Ardour is definitely the way to go. Install it from synaptic if you haven't done so already. If you need help with that, just ask.

2. Have you installed qjackctl? What are your settings?

3. The point of my prior suggestion re: record a track on Ardour via the FireWire Solo is so we can see EXACTLY how far the signal makes it. Folow those steps, and if you find anything ambiguous, please say so and I'll walk you thru it.

4. Do you get sound if you plug headphones directly into the FireWire Solo???

It really isn't constructive for others reading this thread, and more particularly for your own edification, to post that you're giving up, returning to ms and frustrated without ever explaining your problem or taking a few quick steps to provide additional info.Take a sec and respond to the points above and let's get you up and running - once  you actually get to using the device you'll quickly appreciate the small effort was worth it...

Hope to hear from you.

---

### Post by pedrogent on 2008-03-02
> **WestCoastSuccess said:**
> Lol - you give up pretty easily - I switched to Ubuntu less than a year ago and it's FAR easier than anything ms produces.

I can't see where you've posted at which point you're having problems - did you try my suggestions in the prior post? I'm more than happy to help - just take a moment and describe how far you got.

1. Do you have Ardour installed? I presume you have a FireWire Solo in order to record music, and Ardour is definitely the way to go. Install it from synaptic if you haven't done so already. If you need help with that, just ask.

2. Have you installed qjackctl? What are your settings?

3. The point of my prior suggestion re: record a track on Ardour via the FireWire Solo is so we can see EXACTLY how far the signal makes it. Folow those steps, and if you find anything ambiguous, please say so and I'll walk you thru it.

4. Do you get sound if you plug headphones directly into the FireWire Solo???

It really isn't constructive for others reading this thread, and more particularly for your own edification, to post that you're giving up, returning to ms and frustrated without ever explaining your problem or taking a few quick steps to provide additional info.Take a sec and respond to the points above and let's get you up and running - once  you actually get to using the device you'll quickly appreciate the small effort was worth it...

Hope to hear from you.

Hi WestCoastSuccess. I appreciate your help.

I don't know if I would say that I'm giving up easily. And I can't agree with you (yet) that Ubuntu is 'FAR easier than anything ms produces'. I hope that it gets that way and this is the reason I periodically check back every half year or so on my main rig. This is also the reason that I have a few computers running Linux in my home to see what the state of play is. I believe (just my opinion mind you) that Linux is pushing people away because it hasn't sorted out some pretty basic stuff yet. That's OK but if it wants to attract the general public it's no good.

I've read on this forum (and others) for perhaps 20 hours concerning this issue. The time I've actually spent tinkering around in addition would be around 8-10 hours. For me, this is a fair effort when under Windows it would take me about 3-5 minutes to get sound up and running.

I did try your suggestions. They didn't work unfortunately.

I did have Ardour installed. I did have qjackctl installed. I didn't get sound.

Sorry to all those who would attempt to install M-Audio FireWire Solo on Ubuntu if I've put you off. Please try and go for it if you wish. On the other hand, you should know that you won't be hearing any sound out your speakers for a period I think is unreasonable if you choose to do so.

---

### Post by WestCoastSuccess on 2008-03-02
Are you getting sound via the headphone jack on front of FireWire solo?

Also, make sure the power plug remains plugged in at all times...

I'm going to post a new thread outlining, step by step, how to set up a FireWire Solo, along with common roadblocks and their solutions - there's 3000+ views of this thread so seems worthwhile - will make some time tomorrow...

PS it's off topic, but did you happen to notice ms' warning about sp1 for vista? Seems it's going to break a bunch of programs - no doubt that'll take some tinkering and hours... :)

---

### Post by pedrogent on 2008-03-02
Hey WestCoastSuccess,

I have three problems and they are: a) my headphones are back in the UK and I'm in Australia; b) my power plug is nowhere to be found as I've always powered the unit over the bus; c) I've wiped Ubuntu and put XP x64 back on my main rig.

A wiki would be **great** on this particular topic I reckon.

Threads are good but wikis are far more helpful in my opinion.

Thanks for all your help on this. I'll try again in about six months I guess.

PS: Re: Vista SP1... that's why I run XP.

---

### Post by WestCoastSuccess on 2008-03-02
Fair enough - if you decide to try again, please post your results or send me a private message to let me know and I'll give you a hand.

Out of curiosity, why not set up a dual boot system with ubuntu & XP?

---

### Post by pedrogent on 2008-03-02
I did try for quite a while to get a dual boot set-up going using gParted & Super GRUB but couldn't get it to work for some reason.

Perhaps next time I'll use separate HDDs and switch boot priorities in BIOS. Or better yet, run XP virtually from inside Linux.

But to be honest, my main aim is to get off Windows for good and to be able to make Linux do what I want it to do for me. Like I say, I will definitely try again in the future and I will continue to run the other two Linux distros I have going at home. (These ones don't need a IEEE 1394 soundcard.)

I love Linux but for non-tech savvy people like me with a slightly odd hardware arrangement it ain't quite there yet.

---

### Post by WestCoastSuccess on 2008-03-21
I'd encourage you to try Hardy Heron, Ubuntu's next release, due April 24th. It includes the following, which may make your transition easier:

**Wubi**

  There is a new installation option for Windows users. [Wubi]("http://wubi-installer.org/") allows users to install and uninstall Ubuntu like any other Windows application. It does not require a dedicated partition, nor does it affect the existing bootloader, yet users can experience a dual-boot setup almost identical to a full installation. Wubi works with a physical CD or in stand-alone mode, by downloading an appropriate ISO to install from. It can be found on the root of the CD as Wubi.exe. A full installation within a dedicated partition is still recommended, but Wubi is a great way to try Ubuntu for a few days and weeks before committing dedicated disk resources.  
  [IMG]https://wiki.ubuntu.com/HardyHeron/Beta?action=AttachFile&do=get&target=wubi.png[/IMG]

---

### Post by WestCoastSuccess on 2008-03-24
OK, at long last I put together as complete a set of instructions as I could on setting up an M-Audio FireWire Solo with Ubuntu/Linux - you can find it here:

[http://westcoastsuccess.wordpress.com/category/recording/](http://westcoastsuccess.wordpress.com/category/recording/)

I welcome any comments/questions.

Cheers!

---

### Post by X-dark on 2008-04-04
[[IMG]http://brainstorm.ubuntu.com/idea/2800/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/2800/)

---

### Post by TheDriller on 2008-05-15
hi, 
im still not getting anything in the headphones,
signal is fine in ardour and i've set up the connections as shown but i cant hear anything.

i monitor exclusivly on headphones so if i cant get this to work then its back to windoze for me:(

---

### Post by dspiteri on 2008-05-20
> **zbyszek_zbl said:**
> Hi. I've managed to run FireWire Solo on my friend's ubuntu, but there is something strange ;-). First we had to boot into Windows and enable firewire solo under windows. After that Ubuntu started to see firewire solo in hardware manager and it started to work. Earlier I used my FW Solo with MacOS X and during first start mac driver updated firmware. After that it was working without problems with Mac, but no with Linux. Enabling it under Windows was in fact loading another firmware by Windows driver and it looks like Ubuntu works olny with tis windows version.

I can confirm this behaviour. I bought a Solo second-hand and could see it in gscanbus and managed to get it up with Jack, but no sound. I assumed it was the internal mixer settings so I hooked it up to a Mac which loaded new firmware on connection but then worked fine.

When I plugged back in to my Ubuntu system, gscanbus couldn't recognise it any longer. So don't plug in to a Mac unless you have a windows system handy. You also need to set the mixer with a Windows host to get audible sound.

---

### Post by TheDriller on 2008-05-20
> **dspiteri said:**
> I can confirm this behaviour. I bought a Solo second-hand and could see it in gscanbus and managed to get it up with Jack, but no sound. I assumed it was the internal mixer settings so I hooked it up to a Mac which loaded new firmware on connection but then worked fine.

When I plugged back in to my Ubuntu system, gscanbus couldn't recognise it any longer. So don't plug in to a Mac unless you have a windows system handy. You also need to set the mixer with a Windows host to get audible sound.


do you mean that loading new firmware (from windows) will make this fully operational?

and what do you mean in regards to windows?
do you plug into a windows machine, set up the internal mixer as you like it and then plug it into an Ubuntu machine??

im desperate to get this working fully. so far the sound gets in fine but i cant hear anything in the headphones and from my prior experience with this device that is probably a matter governed by the internal mixer setting.

---

### Post by dspiteri on 2008-05-21
> **TheDriller said:**
> do you mean that loading new firmware (from windows) will make this fully operational?

and what do you mean in regards to windows?
do you plug into a windows machine, set up the internal mixer as you like it and then plug it into an Ubuntu machine??

im desperate to get this working fully. so far the sound gets in fine but i cant hear anything in the headphones and from my prior experience with this device that is probably a matter governed by the internal mixer setting.

The OSX firmware bricks the device as far as Linux is concerned, gscanbus and freebob can only see the Solo after the Windows driver loads its firmware. Mixer settings appear to be persistent after they are set from the Windows driver, although I am not having much luck getting Jack apps working with the device.

In fact, to say that the Firewire Solo works with Linux is misleading to the point of being disingenuous: it is fiddly and barely functional with Ardour, doesn't seem to work with any other Jack apps. Lack of Alsa support is a total chore and to top it off, without a Windows boot handy you might as well hook it up to your c64 for all the use you'll get out of it.

I've been running Linux since Debian 1.3 and hoped that one day I'll be able to do at least some tracking. This isn't pro-audio, that's for sure.

---

### Post by X-dark on 2008-05-21
I would be interrested to know the firmware version of people succeeding to make the FW solo works with Ubuntu.
Mine is 2007/08/08 13:56:28 but I can't make it works with Ubuntu

---

### Post by dspiteri on 2008-05-22
> **X-dark said:**
> I would be interrested to know the firmware version of people succeeding to make the FW solo works with Ubuntu.
Mine is 2007/08/08 13:56:28 but I can't make it works with Ubuntu

I can get it working only after hooking up to Windows, the OSX firmware jams it up for Linux use. I can confirm that it does work OK but you first need to set the internal mixer with Windows and then connect to Linux without powering it off. Do these and it will work.

I believe FFADO will incorporate some mixer controls for bebob which will alleviate some of these issues. Until then have some windows handy.

---

### Post by X-dark on 2008-05-23
I'm not so sure about FFADO.

[QUOTE=http://www.ffado.org/?q=release/beta]Features

    * 24-bit audio input/output (unlimited number of channels)
    * supports for all sample rates a device supports
    * MIDI input/output (unlimited number of channels)
    * Support for S/PDIF and ADAT/SMUX I/O
    * Support for external sync (e.g. Wordclock)
    * [B]Internal mixer and device control support for all officially supported
      devices[/B] (NOTE: no support for internal effects DSP)
    * Support for device aggregation (limited to devices on the same bus that are synced externally)
[/QUOTE]

And The FW Solo is only in the "reported to work" section, not in the "supported" one.

---

### Post by dspiteri on 2008-05-24
> **X-dark said:**
> I'm not so sure about FFADO.



And The FW Solo is only in the "reported to work" section, not in the "supported" one.

I've reported this behaviour to the FFADO team as I haven't seen it documented coherently anywhere. I have also suggested to M-Audio that it would be nice if they could provide info to the FFADO developers.

Other people who wish to see this good-value device supported should also throw their two-cents worth at M-Audio.

---

### Post by X-dark on 2008-05-24
All right I will write an e-mail to them.

---

### Post by X-dark on 2008-05-24
From the FFADO mailing list (2008-03-14):

> > freen sent a message using the contact form at
> [http://www.ffado.org/?q=contact](http://www.ffado.org/?q=contact).
>
> Hi,
> I own an M-AUDIO firewire 1814 and it's the only thing keeping me with a
> dual boot.
> I contacted a support dude at M-Audio and they wish to know what
> information you require to get it working under Linux.
Please ask them to contact me at pieter/palmers\ffado/org (/=., \=@).
I will drop by their booth and try to get hold of someone.

Greets,

Pieter

Things may be moving

---

### Post by denn O))) on 2008-05-24
Hi to all. I found very useful this thread to almost use my m-audio solo with linux. I have to say ALMOST. the fact is that with ardour i can record (i can see the wave on the track), but no way having the sound out. I post my screen with the connection of jack.
I use ubuntustudio 8.04. activated an option witch says "Enable raw 1394".
The first difference i noticed is the name of the connections in qjactl.
Thanks in advance.denn

---

### Post by TheDriller on 2008-05-24
> **X-dark said:**
> From the FFADO mailing list (2008-03-14):



Things may be moving

Thats pretty cool,
i tried to compile ffado but it just made a mess out of jack. i look forward to seeing this work but i reckon for the forseeable future i'll be back on filthy old windoze.

---

### Post by TheDriller on 2008-05-24
> **denn O))) said:**
> Hi to all. I found very useful this thread to almost use my m-audio solo with linux. I have to say ALMOST. the fact is that with ardour i can record (i can see the wave on the track), but no way having the sound out. I post my screen with the connection of jack.
I use ubuntustudio 8.04. activated an option witch says "Enable raw 1394".
The first difference i noticed is the name of the connections in qjactl.
Thanks in advance.denn

dude, its kinda hard to see in your picture, but you need to be making a connection between "Ardour" on the LEFT and "System" on the RIGHT. (System might be called "Freebob" on your setup).

also, note that a lot of people are having trouble with getting the headphone output to work.

---

### Post by dspiteri on 2008-05-25
> **denn O))) said:**
> Hi to all. I found very useful this thread to almost use my m-audio solo with linux. I have to say ALMOST. the fact is that with ardour i can record (i can see the wave on the track), but no way having the sound out. I post my screen with the connection of jack.
I use ubuntustudio 8.04. activated an option witch says "Enable raw 1394".
The first difference i noticed is the name of the connections in qjactl.
Thanks in advance.denn

Patch to playback_3 and playback_4, 1 and 2 are the SPDIF channels. This default order is something that should be fixed...

---

### Post by X-dark on 2008-05-29
> **dspiteri said:**
> Other people who wish to see this good-value device supported should also throw their two-cents worth at M-Audio.

I've got the response but it seems to be a generic one. I've written them back.

> Cedric,

M-Audio uses a 3rd-party Vendor for Unix support.

4Front Technologies develops and supports Unix drivers for our Revolution and Delta series of products.

The software is available for free evaluation and non-profit use but 4Front charges a fee for technical support and commercial use.

They can be found at the following web address:
[http://www.opensound.com]("http://www.opensound.com")

There are also Linux drivers available for some of our products on this website:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix) (the right link is [http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio"))

Please note that M-Audio does not endorse the use of these drivers and we have no direct involvement in developing them.

Best regards,

---

### Post by dspiteri on 2008-05-31
Yeah they sent me a generic blah-blah as well. I simply pointed out to them that they don't have to do anything except answer questions for the FFADO guys.

Here's hoping because it really is a sweet sounding device, especially after using a Tascam US428 for years...

---

### Post by WestCoastSuccess on 2008-07-05
The M-Audio FireWire Solo does work, and very well, with Linux - mine runs flawlessly, in fact - no X-Runs and a latency of just 2ms.

If you're having trouble getting sound when playing back Ardour, MAKE SURE YOU'VE DISABLED THE TRACK(S) FROM RECORDING IN ARDOUR. This means the red "arm for recording" square in the track is not lit up. If you don't do this, you won't get playback, since the track remains enabled for recording, which mutes playback.

If you can record waveforms in Ardour but can't hear them (and you've followed the step above), you're 99% of the way there. Click “Options” from Ardour’s menu bar, select “Monitoring” and pick “Software Monitoring”.

You can also check the Troubleshooting section at:

[http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/](http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/)

M-Audio is now directing their Linux customers to these instructions for guidance.

Cheers.

---

