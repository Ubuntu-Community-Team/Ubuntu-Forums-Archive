---
title: "[SOLVED] No sound output on Toshiba S5804"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by crumbb on 2008-04-03
I've read everything I can find, including the comprehensive guide that's stickied, and I can't get this working.

I have a Toshiba A205 S5804 laptop. When I run aplay -l I get:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I can run alsamixer and I've made sure that none of the channels are muted.
I've also confirmed that the current user is in the /etc/group.
When I run Amarok I can hit play and the graphic equalizer shows that Amarok is playing the sound.

I don't get any kinds of errors, but nothing comes out of the speakers. Any ideas/suggestions.

---

### Post by LODRazor on 2008-04-03
I also have a very similar problem, my sound device is ALC861VD.  I have done everything that you have done, to no avail.  Everything points to the sound card being installed correctly, but no sound.  I have a dual boot system with Win XP Pro and the sound works fine in XP.  I know this is no help to you, but at least you are not the only one.  Hopefully someone will be able to help us.

---

### Post by crumbb on 2008-04-03
Yeah, the sound was working in Vista before I upgraded. I'm new to linux but I managed to get the wireless working. I'd rather use the laptop without sound than go back to Vista.

---

### Post by tangibleorange on 2008-04-03
do you have no sound at all, or sound from just the laptop speakers but no headphones (or vice versa)? could you type the following command into a terminal:

```
alsamixer
```

into a terminal and tell me what version of ALSA you are running (should be at the top)

---

### Post by crumbb on 2008-04-03
I get no sound out of the speakers or the headphones no matter weather the headphones are plugged in or not. 

I have AlsaMixer v1.0.15

---

### Post by tangibleorange on 2008-04-04
OK. Could you type this into a terminal:

```
gksu gedit /etc/modprobe.d/alsa-base
```

You should then open up your alsa-base file in the gedit text editor. Scroll down to the bottom and add this line:

**options snd-hda-intel model=toshiba**

then save the file, close and reboot. hopefully you'll have sound!

---

### Post by crumbb on 2008-04-04
I added the options... line to alsa-base and rebooted, but got no change. There are no errors, Amarok acts like it's playing, all the sound levels are at max on the mixer, but no sound comes out of the speakers or headphones.

BTW, I'm currently using the Hardy beta, but I get the same problem with Gutsy and vanilla ubuntu.

---

### Post by tangibleorange on 2008-04-04
OK... My only suggestion I'm afraid is to keep adding different option lines to alsa-base and hoping for the best! This is one that works for some people:

**options snd-hda-intel model=3stack**

After that, I'm out of ideas. You could try updating to ALSA 1.0.16, which I will be happy to help you with  :).

---

### Post by crumbb on 2008-04-04
OK, I don't know what happened, but I rebooted after adding some totally unrelated samba packages and the sound is working. I rebooted again to make sure it took, and sound is still working. I guess some mysteries weren't meant to be solved.

Thanks for your help everyone. As far as I'm concerned you can mark this "solved."

---

### Post by tangibleorange on 2008-04-04
> **crumbb said:**
> OK, I don't know what happened, but I rebooted after adding some totally unrelated samba packages and the sound is working. I rebooted again to make sure it took, and sound is still working. I guess some mysteries weren't meant to be solved.

Thanks for your help everyone. As far as I'm concerned you can mark this "solved."

LOL fair enough! some things don't make sense I guess. BTW, you have to mark the thread solved - it's under "thread tools" i think! :)

---

