---
title: "m-audio usb - no output sound"
date: 2013-04-12
forum: Hardware
---

### Post by kralgi on 2013-04-12
I am quite new in this forum, but recently i've purchase an m-audio fast track pro sound card and happily it got loaded automatically in my ubuntu but yet for some reason I can't hear no output sound at my media players and websites like youtube. but strangely when I installed the hydrogen drum machine, it would give me an output sound only within the program itself. has anyone ever used and configured this audio card on linux? 

here are some specs -

[CODE ] aplay -l [/CODE]
```
 **** List of PLAYBACK Hardware Devices ****
card 0: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 2: VT1708S HP [VT1708S HP]
  Subdevices: 1/1

```

```
chupacabra@thejungle-MS-7592:~$ lsusb
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 002: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 003 Device 003: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 004 Device 002: ID 0763:019a Midiman Axiom 61
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by kralgi on 2013-04-12
and here's the output of 
```

wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```


[http://pastebin.com/qQDa7gJG](http://pastebin.com/qQDa7gJG)

---

### Post by kralgi on 2013-04-13
anyone? please?..

---

### Post by gordintoronto on 2013-04-14
What version of Ubuntu? Is the card selected in Sound Settings? Normal volume, not muted? Did you install the restricted extras?

Firefox browser? What media player? (I find that VLC often starts up with sound muted, and it gives no indication about it.)

---

### Post by kralgi on 2013-04-20
Linux home-MS-7592 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 20:00:05 UTC 2013 i686 i686 i686 GNU/Linux

Yes, the card is selected and not muted. Been trying all kind of media players and different browsers also. 
What are these restricted extras you've been talking about ?

---

### Post by gordintoronto on 2013-04-21
Is it true that you are using 32-bit Xubuntu 12.10? If not, ignore the rest of my message.

If you run the Synaptic Package Manager and search for "restricted extras," I think one of the results will be Xubuntu Restricted Extras. This is needed to play MP3s, for example.

---

### Post by kralgi on 2013-04-21
Installed it, still not working.

---

### Post by kralgi on 2013-04-29
anyone?.. please..

---

### Post by Thee on 2013-04-29
Maybe PulseAudio is the problem. If Hydrogen uses ALSA and rest of the applications PulseAudio it would explain why you hear sound only from there.. Try setting audio options in VLC to play using ALSA and see if it produces any sound then.

---

