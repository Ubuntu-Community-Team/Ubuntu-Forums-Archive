---
title: "Headphones &amp;&amp; Speakers problem (different)"
date: 2008-09-25
forum: General Help
---

### Post by d4ni on 2008-09-25
Hi there, I got the same problem like some other users in this forum but this one is a little different.

When I connect my headphones my speakers wont mute. So I read several threads about the same problem but I have a "small" difference.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
Subdevices: 0/1
Subdevice #0: subdevice #0

```

Model = Generic -.-"


Output for head -n 1 /proc/asound/card0/codec*
```
Codec: Realtek ID 272

```

This codec won't appear on the ALSA list needed to edit the alsa-base

Any ideas??  Thanks.

---

### Post by d4ni on 2008-09-26
/bump

---

### Post by d4ni on 2008-09-28
=/

---

### Post by cubeek on 2008-10-19
I have exactly the same problem. I've been trying fix it almost a month and the speakers are still playing while the headphones are plugged in. What laptop do you have. I have Toshiba Qosmio F50-108. I wrote on many forums but nobody knows what to do.

---

### Post by saygin on 2008-10-22
hi, 
I have toshiba qosmio x305 and i have the same problem. But I guess it is not gonna be solved soon because alsa doesn't have support for realtek Id 272 for now. So we have to wait until this is solved... :(

---

### Post by cubeek on 2008-10-23
That's very bad :( I hope that alsa will develop support for this snd card soon :-/

---

### Post by Chakotay on 2008-11-17
Thanks to a [_wordpress blog_](http://nc10ubuntu.wordpress.com/2008/11/11/what-i-did/#comments) I found [_this thread_](http://ubuntuforums.org/showthread.php?t=962695) which appears to have a workaround. I haven't tried it personally, I'll post here tonight if it works for me.

---

### Post by saygin on 2008-12-01
Hi all,
As I said before, I have toshiba qosmio x305-q701 laptop. I installed ubuntu 8.10 on it. I had the same problem with ubuntu until I downloaded and compiled newest alsa codec pack. There is no problem right now. I don't know if it will be added to repos soon, but it is not hard to compile manually.

---

### Post by Ryuki_NdranC on 2009-01-23
> **saygin said:**
> Hi all,
As I said before, I have toshiba qosmio x305-q701 laptop. I installed ubuntu 8.10 on it. I had the same problem with ubuntu until I downloaded and compiled newest alsa codec pack. There is no problem right now. I don't know if it will be added to repos soon, but it is not hard to compile manually.

Hi there, i bought a toshiba qosmio x305-q705 and i found myself in the same situation. When i plug in the headphones the speakers won't mute.

When i do 

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
Subdevices: 0/1
Subdevice #0: subdevice #0
```

i got the same response as d4ni (idk if thats... bad... should show realtec or something?)

In your thread you state you found a workaround by installing compiling the latest alsa drivers (i guess this ones arent in the official repos). Do you mind pointing me out to a detailed HOWTO-like guide of sorts. I'm pretty new to the ubuntu world and i quite don't get whats the problem.

Is it that my audiocard works with a "generic" type of driver?. Thats why it sounds but has several bugs?. Does the subwoffer works with ubuntu? I mean do i get the same high quality sound as with crappy ol' windows?

Im srry if i bumped this and i shouldn't, but it seems better than makeing a hole new thread.

EDIT: I don't know if this would help but this is the output of my 

"head -n 1 /proc/asound/card0/codec*"

```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 272

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

```

---

### Post by cubeek on 2009-03-07
> **saygin said:**
> hi, 
I have toshiba qosmio x305 and i have the same problem. But I guess it is not gonna be solved soon because alsa doesn't have support for realtek Id 272 for now. So we have to wait until this is solved... :(

Did you changed anything in /etc/modprobe.d/alsa-base ? I mean snd-hda-intel model parameter. I have qosmio f50-108, compiled alsa-driver, utils and libs 1.0.19 and the speakers still doesn't mute, when I plug headphones.

---

