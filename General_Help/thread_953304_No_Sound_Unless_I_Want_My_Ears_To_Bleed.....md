---
title: "No Sound Unless I Want My Ears To Bleed...."
date: 2008-10-20
forum: General Help
---

### Post by Aflack on 2008-10-20
anytime any sound plays through my speakers on my monitor, it echos and is staticy. this means youtube and videos, all seriously hurt to listen to. any ideas? please help...EDIT: ill be back in about 6 hours, its almost 1, and im tired. post.

---

### Post by p_quarles on 2008-10-20
Well, first of all, did you buy this computer with Ubuntu, or did it have another OS previously? Did these speakers work better in the previous OS?

Second, each sound card has its own characteristics, but I'd try turning down the PCM channel. Gnome's mixer application should show it, but a foolproof method that will work in nearly any modern Linux setup is to run:
```
alsamixer
```
and then switch over to the PCM line and turn it down.

---

### Post by northern lights on 2008-10-20
Should it have worked better under any other OS or previously on GNU/Linux also, there's one more information request I'd like to add:

Is it only certain videos and youtube (video web content) or does this happen when playing local audio (mp3/ogg) also?

---

### Post by Aflack on 2008-10-20
northern lights, i already said any sound that tries to play is messed up, and i tried the pcm thing but still has the same noises and echo. anymore ideas?

---

### Post by northern lights on 2008-10-20
Can you please post the output of ```
sudo lshw -C multimedia
```
Thank you.

---

### Post by Aflack on 2008-10-20
```
  *-multimedia            
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

```

I got that

EDIT: now im going to school post your replies, ill be back in a few hours.

---

### Post by p_quarles on 2008-10-20
You still haven't answered my first. question.

---

### Post by Aflack on 2008-10-20
im dual booting vista and it works ok in vista

---

### Post by Aflack on 2008-10-20
help anyone

---

### Post by Aflack on 2008-10-21
please??

---

### Post by niteshifter on 2008-10-21
Hi,

FWIW, I get echoes and noise if analog loopback is on, so maybe yours is on?

Volume Control, Switches Tab.

---

### Post by Aflack on 2008-10-21
nope, i only have the headhpones option

---

### Post by Aflack on 2008-10-22
no one??

---

