---
title: "No sound from right speaker"
date: 2014-06-27
forum: Hardware
---

### Post by maazmahmood on 2014-06-27
It works fine on windows. I have the Creative Sound Blaster Live! 24 Bit sound card. I have two speakers and my right one won't work. Everything else works. Whenever I plug in headset that works just fine. It's this that's having problems for some reason. Any ideas?

---

### Post by E_Sound on 2014-06-27
Have you checked 'alsamixer' settings (type in terminal)? Gain level of one of the channels might be decreased.

---

### Post by gordintoronto on 2014-06-28
Sounds like a broken wire. Could you plug the speakers into another device to check that they both work?

---

### Post by maazmahmood on 2014-06-28
I have pulseaudio not alsa :/

---

### Post by maazmahmood on 2014-06-28
I have pulseaudio not alsa :/

It works in Windows, both of them

---

### Post by maazmahmood on 2014-06-30
Hate to do this but bump

---

### Post by Yellow Pasque on 2014-07-01
Possibly related: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1334365](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1334365)
> I have pulseaudio not alsa :/
You have both.

---

### Post by maazmahmood on 2014-07-01
That actually does seem close to my problem. Although I don't know what Raymond is saying in the second to last post

---

### Post by maazmahmood on 2014-07-11
When i type in alsamixer under playback it says 
"This sound ddevice does not have any playback controls"

---

### Post by Yellow Pasque on 2014-07-11
You may have to press F6 to change devices. Otherwise, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by maazmahmood on 2014-07-11
I have the Sound Blaster Live! 7.1 24 bit sound card. I don't see it when I hit F6
**Update** Ok I got it, it was CA0106, for some reason. And I increased Analog F to the the highest and brought it back down and they were synced then. Thanks :)

---

### Post by Yellow Pasque on 2014-07-11
You're welcome. Please mark thread solved if the settings hold after reboot.

---

