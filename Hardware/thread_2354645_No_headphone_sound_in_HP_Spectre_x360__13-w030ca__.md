---
title: "No headphone sound in HP Spectre x360  13-w030ca  Ubuntu 16.10"
date: 2017-03-04
forum: Hardware
---

### Post by destevez on 2017-03-04
Hello!

I've been struggling for several days with this issue. According to many posts the HP Spectre x360 works great with 16.10 and it does but this is the only problem i have (although a big one). Plugging in the headphones make speakers mute (ok) but no sound ever comes out from the headphones. I have Dual Boot with Windows 10 with Fast Startup disabled and headphone works ok in Windows (last Realtek drivers installed) so hardware problem is discarded.

Some more info
[LIST]
[*]The laptop detects when the jack is connected and disables speakers. I can "see the sound" in headphones section with pavucontrol  and all seems right with alsamixer, no muted stuff
[*]Tried changes with hdaJackRetask, alsa-base.conf and alsa-mixer/paths/analog-output-headphones.conf but just trying my luck with those since it's not clear what should i change
[*]I also tried reinstalling alsa and pulseaudio
[/LIST]

My alsa info [http://www.alsa-project.org/db/?f=2bf7d419b3033dd2c9268c910d7cd776c87009c6](http://www.alsa-project.org/db/?f=2bf7d419b3033dd2c9268c910d7cd776c87009c6)

Any clues on this? I'm totally lost...

Thanks everyione!

---

### Post by davidquantum on 2017-03-04
I had exactly the same problem with my Spectre x360. It got already frustrating until I found a suggestion [here]("https://ubuntuforums.org/showthread.php?t=2168853") to add to */etc/modprobe.d/alsa-base.conf* the following line
```
options snd-hda-intel model=auto

```
restarted the machine, and now the headphones work fine.

---

### Post by destevez on 2017-03-04
Thanks for the suggestion, that was one of the first things i tried. I even tried with model=laptop, hp or generic 

I tried it again now restarting too but no luck, we must have different Spectre models i guess...

---

### Post by davidquantum on 2017-03-04
You probably already have already done it, but just in case, I had to do those steps first as well: [http://askubuntu.com/questions/716231/no-sound-in-ubuntu-on-hp-spectre-x360](http://askubuntu.com/questions/716231/no-sound-in-ubuntu-on-hp-spectre-x360)

---

### Post by pantherattack on 2017-03-05
Nothing to contribute to the solution, but just wanted to let the OP know they are not crazy: I have basically exactly the same setup (13-w030ca, ubuntu 16.10, windows dual boot with hardware working in windows) and the mentioned candidate solutions do not work for me either. Pllugging headphones in turns off speakers, but nothing comes through headphones. (same problem in kernels 4.8 and 4.10, however 4.10 gets auto-rotation working)

---

### Post by destevez on 2017-03-05
Thanks again davidquantum and pantherattack,

I also read about the grub config but didn't want to mess around with grub since that solution mentioned a different sound card and Spectre model. Did you try that too, pantherattack?

It really seems a problem with this later model... i couldn't care less about auto-rotation but i need music to program! :P

---

### Post by destevez on 2017-03-07
Has anyone tried some bluetooth headphones? That'd be another option but not sure if this model will have problems too!

EDIT> BT headphones work ok.

---

### Post by 1rdc on 2017-06-29
So did anyone find a fix? I can't even use bluetooth earphones since my bluetooth doesn't work either :/ I'm still on kernel 4.8.6

---

