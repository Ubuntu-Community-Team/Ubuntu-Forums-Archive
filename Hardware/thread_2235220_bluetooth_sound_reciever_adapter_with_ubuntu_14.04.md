---
title: "bluetooth sound reciever adapter with ubuntu 14.04 not working"
date: 2014-07-19
forum: Hardware
---

### Post by brettmichaelis on 2014-07-19
Hi,

I got a bluetoohsound reciever and it paired fine in ubuntu 14.04 but its not playing sound through the bluetooth sound reciever.

I tried everything but it wont play through the bluetooth sound reciever
The bluetooth settings in ubuntu shows that the bluetooth sound adapter is sucessfully paired but its not working


Is there anything i can do

---

### Post by brettmichaelis on 2014-07-20
anyone?

---

### Post by jeremy31 on 2014-07-20
Have you tried this?
```
pactl load-module module-bluetooth-discover
```

It seems to make some audio devices work

---

### Post by armando5 on 2014-09-02
[COLOR=#333333][FONT=monospace]Had the same problem fixed it with:
"pactl list cards short" to get the device id
then I did "pactl set-card-profile x a2dp"
where X is your device id[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]found it by reading
[http://askubuntu.com/questions/203272/no-a2dp-streaming-audio-from-12-04-to-bluetooth-headset](http://askubuntu.com/questions/203272/no-a2dp-streaming-audio-from-12-04-to-bluetooth-headset)[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2014-09-02
All good suggestions but let's clear out the obvious first, shall we?
Have you, after pairing, selected the new audio device as output (Ubuntu with Unity -> Sound indicator > sound settings)? It isn't automatic.

---

