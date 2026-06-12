---
title: "Getting my firewire audio card working"
date: 2009-07-13
forum: Hardware
---

### Post by Virus_ST on 2009-07-13
Hello, good people of the Ubuntu community. I've recently switched from Windows XP (which I've been using for 10 years) to Ubuntu. The reasons I switched are of the ideological and political nature. I'm pretty much a newb (I've read most of the Ubuntu pocket guide though, if that counts) and as you can imagine I'm having a rough time with the aforementioned intention.

I have installed jack, freebob, ffado, followed most of the online instructions - at least the ones I could understand - to get my M-Audio Ozonic to work with no success. I believe that my TI 1394 controller wasn't even detected because I can't see it in the device manager at all and can't find the raw1394 folder in the /dev folder (forgive me if I'm being stupid).
Here's the message I get when I type ```
jackd -d freebob
``````
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: No such file or directory
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
```I'm sure you've all seen this before, so sorry for posting it once more. This is where I tried getting help [http://parumi.wordpress.com/2006/12/19/getting-firewire-audio-work-on-linux/]("http://ubuntuforums.org/parumi.wordpress.com/.../getting-firewire-audio-work-on-linux/") and got stuck in the part after this message shows up.

---

### Post by Virus_ST on 2009-07-13
Ok, disregard the first post. I've installed ffado and jack. I can get the ffado mixer running and it has picked up the Ozonic. I've handled the raw1394 issue and now I'm clueless. When I open qJackCtl, in the "Connect" window, under Audio or MIDI I see no Readable Clients/Output ports or Writable Clients/Input ports, while under ALSA I see something called MidiThrough. Also in the "Setup" window, I don't know what driver I should use. I've scourred through the net and I really don't have any idea how this is supposed to work. I'm getting tired and angry here and seriously considering head butting the screen.

Please, anybody...

---

