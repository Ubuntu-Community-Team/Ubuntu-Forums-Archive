---
title: "Sound on Asus V1S"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by vange on 2007-10-19
Hi

Today I installed Kubuntu 7.10 64-bit on my brand new Asus V1S. Everything works out of the box (though I haven't tried using the webcam yet), but the speakers behave strange: when I plug the hear phones, the speakers continue to play. The laptop uses the Intel 82801H (ICH8) chipset.

What kind of info do you need for helping?

Thank you for any help.

---

### Post by TorbX on 2007-10-21
I have the same problem with:

Asus V1S
Ubuntu 7.10 32 bit
ALSA 1.0.15

**head -n 1 /proc/asound/card0/codec#***
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC660-VD

==> /proc/asound/card0/codec#1 <==
Codec: Generic 1543 Si3054

---

### Post by vange on 2007-10-22
I get the same output

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC660-VD

==> /proc/asound/card0/codec#1 <==
Codec: Generic 1543 Si3054

---

### Post by ZennouRyuu on 2007-10-26
Sound is functioning properly on 32-bit Gutsy

---

### Post by TorbX on 2007-10-26
> **ZennouRyuu said:**
> Sound is functioning properly on 32-bit Gutsy

I use 32-bit Gutsy too and it's not working. Does it work out of the box for you?

---

### Post by lapsey on 2007-10-26
I have found that Gutsy likes to play around with group permissions.

Check if this has happened by looking at /etc/group: *cat /etc/group | grep audio*

In an ideal world you should get **audio:x:29:username**

If your user name does not appear at the end, edit that line to reflect your username: *sudo nano /etc/group*

I seem to do this very often for my problems!

---

### Post by TorbX on 2007-10-27
I'm already in that group. I also have Sound, but when I plug in the headphones, the loudspeakers don't turn off. So I can hear everything on both, the headphones and the loudspeaker.:(

---

### Post by vange on 2007-10-28
I am also in the audio group. And my sound behaves just like TorbX.

---

### Post by Tha Tawa'S on 2007-12-27
Hello,
i got my brand new asus too and i se gutsy gibbon 7.10-32bits.
I go the same problem.
when i plug an headset, sound is in headset and speakers.
Has anyone found a solution 2 months later ??
thanks.

---

### Post by vange on 2007-12-28
I have not resolved my issue yet. I have even tried a solution which required me to install Alsa from source, with no luck - so don't do that, as I haven't found a way to go back to the Alsa-version supplied by Kubuntu.

If I find a solution I will post it in this thread.

---

### Post by Casbah on 2007-12-30
hi

I had the same problem described above with my asus v1s since months
know I found a solution on the following page
[http://yaita.blogspot.com/2007/09/debian-etch-asus-v1s.html](http://yaita.blogspot.com/2007/09/debian-etch-asus-v1s.html)

it's in german, so:
- install alsa-driver-1.0.15
- add/change the following line in /etc/modprobe.d/alsa-base:
  "options snd-hda-intel model=lenovo"

I tried it with alsa-driver-1.0.14 and it works as well

---

### Post by Tha Tawa'S on 2007-12-30
Hello,
thanks for answering.
don't hesitate to post if you have a solution.
we are several V1S users searching one.

---

### Post by Tha Tawa'S on 2007-12-30
> 
  "options snd-hda-intel model=lenovo"

I tried it with alsa-driver-1.0.14 and it works as well

It works with lenovo ??? on my V1S it is a 660stack.
but i will try.
thanks.

---

### Post by vange on 2008-01-02
It didn't work for my laptop. The sound is working (as always), but with a jack plugged in, the speakers doesn't mute.

---

### Post by Casbah on 2008-01-04
> **Tha Tawa'S said:**
> It works with lenovo ??? on my V1S it is a 660stack.
but i will try.
thanks.

I don't really know, why it works on my laptop.
There is still a bug. When I change the volume with the hotkeys, the speakers are turning on with my headphones plugged in. But when I unplug the headphones and plug them in again the speakers are turning off again.
So it's not really a permant solution but at least I don't have to annoy other people with my music any longer ... :wink:

---

### Post by Tha Tawa'S on 2008-01-06
> **Casbah said:**
> I don't really know, why it works on my laptop.
There is still a bug. When I change the volume with the hotkeys, the speakers are turning on with my headphones plugged in. But when I unplug the headphones and plug them in again the speakers are turning off again.
So it's not really a permant solution but at least I don't have to annoy other people with my music any longer ... :wink:

Thank you Casbah,,,, it works fine for me !!!!
i got Ubuntu 32 bits
alsa 1.0.14
bye

---

### Post by HaMF on 2008-03-14
> **Casbah said:**
> I don't really know, why it works on my laptop.
There is still a bug. When I change the volume with the hotkeys, the speakers are turning on with my headphones plugged in. But when I unplug the headphones and plug them in again the speakers are turning off again.
So it's not really a permant solution but at least I don't have to annoy other people with my music any longer ... :wink:
I found a workaround for this Problem:
It seems like the speakers just turn on you change the volume of the "Front" channel. So let's avoid this:
* Go to System > Settings > Audio > choose Device: HDA Intel (...) and Channel: PCM
* If you use the applet in the gnome-Panel to control the volume: Go to [right click] -> Settings -> Device: HDA Intel (...); Channel: PCM
* You may want to turn up the volume of the Front channel to almost 100%

---

### Post by nagrover on 2008-06-24
You guys rock. I'm running Linux Mint Elysa ( Ubuntu 8.04 derivative ) and this fix worked for my V1S. To recap, I didn't need to install anything (no alsa driver etc) and all I had to do was modify the alsa-base file as per Casbah's instructions. Then make the tweak posted by HaMF above. Everything seems to be working as it should and I can now crank my headphones at work! Thanks!

---

### Post by vange on 2008-07-17
Casbah, your fix works for me - thank you a lot! I do not have to apply HaMF's fix.

---

### Post by tintin8 on 2008-07-18
For me works fine too, thank you!! :D

---

