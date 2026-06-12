---
title: "random rythembox crashes with UA-25 usb-audio"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by tempo500 on 2007-05-22
hi,

i am experiencing random crashes with ryhtmbox with an edirol ua-25. it usually plays a few seconds of a song - then crashes. i disabled my onboard-soundcard in the bios, which did not help... i hope there is someone out there with a solution to this. i am glad to provide any relevant information! 

```
phil@render:~$ aseqdump -l
 Port    Client name                      Port name
  0:0    System                           Timer
  0:1    System                           Announce
 14:0    Midi Through                     Midi Through Port-0
 20:0    UA-25                            UA-25 MIDI 1
 24:0    MPU-401 UART                     MPU-401 UART MIDI
```

 
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: UA25 [UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by tempo500 on 2007-05-23
no one?

i had it working yesturday all day, i guess after i reset the soundcard(unplugging the usb). did that today and everything sound related crashes without notice.... aplay -l now lists the ua25 as card 2. yesturday it was on 1... please...phil

---

