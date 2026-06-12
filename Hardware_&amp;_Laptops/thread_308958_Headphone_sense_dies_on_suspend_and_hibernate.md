---
title: "Headphone sense dies on suspend and hibernate"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by MHD on 2006-11-28
Hi All, I'm using Edgy (Kubuntu) on a Dell 6400

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

After suspend and hibernate and some times after the first time a jack is plugged into the headphone out headphone sense ceases to work...
So when I pug in my headphones sound continues to issue from the speakers much to the annoyance of my officemates...

Here is my amixer:
```
imple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 227 [89%]
  Front Right: Playback 227 [89%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%]
  Front Right: 4 [100%]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic'
  Item0: 'Mic'

```

As you can see, and as with alsamixer and kmix the "headphone sense" control is missing!

Any help much appreciated!

---

### Post by MHD on 2006-12-01
Ok, so things seem fairly quite...
I guess I will ask then: Are there any other Dell 6400 (or any other model) Ubuntu users who experience the same problem?

---

### Post by heathmike on 2006-12-07
I have the same problem on my Dell Latitude D820 except the headphone jack only works if I have my headphone plugged in when I boot up the machine.  If I have the machine booted up and plug in the headphones, sound comes out of both the built in speakers and the head phones.  If I unplug the headphones and plug them back in, again the sound comes out of the built in speakers and the headphones.  Nether suspend nor hibernate work for me. :(

---

### Post by charles.figura on 2006-12-15
Yep -
I've got a D620 and I'm experiencing exactly this problem - headphone sense works when I'm on a 'fresh' boot, but when coming back from a suspend the main speakers do not cut out, just as you note.  Same result too - annoyance of others.

---

### Post by RikBlankestijn on 2006-12-21
Exactly the same problem here.

---

### Post by charles.figura on 2007-01-21
Just to give this a bump, I've posted this on launchpad as
[https://bugs.launchpad.net/ubuntu/+bug/80860](https://bugs.launchpad.net/ubuntu/+bug/80860)

---

### Post by hazza96 on 2007-03-10
I get exactly the same problem on a Dell Inspiron 6400. If I boot with the headphones in sound only comes out the headphones but if I unplug and re-insert them or boot with out them in then sound comes out both headphones and speakers.

Is it only Dell's or is it other laptops as well?

---

### Post by Xscratch on 2007-03-11
I have a HP Pavillon dv6297ea...same problem
If I boot up the mahine with the headphones plugged in sound only comes from headphones, but if I unplug them sound comes out anymore...g
if I re-plug the headphones sound comes both from headphones and speakers.

I'm thinking to upgrade to feisty...

---

### Post by chezzo on 2008-03-10
I'm using Gutsy on an Inspiron 640m and have this problem, but only after standby not hibernate. When I bring it back from standby and try to listen to something with headphones plugged in it plays through headphones and speakers, no matter whether the headphones were plugged in coming out of standby or not.

Also, I think the problem with headphones not working if you quickly unplug and plug them back in is a different one as I get it in Windows too. The only solution seems to be to wait for a bit.

---

