---
title: "How I disable on board sound card in 8.10?"
date: 2008-11-09
forum: General Help
---

### Post by rebelrex on 2008-11-09
hi!

I have 2 sound cards: sb live and onboard sound card.
For some reason the onboard sound card which is disabled in bios is detected in ubuntu 8.10, and that gives me problems.
I want to disable it, so ubuntu will think I only have 1 sound card - SB LIVE.

I read somewhere that in older versions what I needed to do is to blacklist the module of the sound card which I dont want to activate.
and that I do by going to :/etc/modprobe.d/blacklist
and adding line:
blacklist modulename

Is this also the way in 8.10?

---

### Post by FreeFull on 2008-11-09
Try disabling it in the BIOS.

---

### Post by Peter09 on 2008-11-09
Yes you should be able to do this.

As already said the best way is to disable the card through the bios. Failing that you can blacklist the driver.

---

### Post by rebelrex on 2008-11-09
thank you for your answers
but as I wrote in my 1st post, it is disabled in the BIOS , i mean , in winxp it doesnt detected..

and how I blacklist it?

---

### Post by Peter09 on 2008-11-09
Can you post the output of the terminal command

```
lshw -C sound
```

---

### Post by kleeman on 2008-11-09
I have had this problem a lot. The solution is to ensure that the onboard soundcard is not regarded (by alsa) as the default card. What I do is edit the file

/etc/modprobe.d/alsa-base

at the bottom of this file you will see a whole bunch of lines like

options snd-intel8x0m index=-2

These ensure that certain soundcards are not the default ones
You need to add your similar line here with the correct alsa module (i.e. the snd-intel8x0m of the above sample line). To figure this out open a terminal and type

lsmod | grep snd

Report the out put and I'll tell you what the replacement for snd-intel8x0m needs to be for your system.....

This can also be found by the 

lshw -C sound

command suggested above. Look for the module=XXXXXX

and XXXX is what you need....

---

### Post by rebelrex on 2008-11-09
> **Peter09 said:**
> Can you post the output of the terminal command

```
lshw -C sound
```

WARNING: you should run this program as super-user.
  *-multimedia:0          
       description: Multimedia audio controller
       product: AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52 module=snd_intel8x0
  *-multimedia:1
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:2
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bttv latency=64 maxlatency=40 mingnt=16 module=bttv
  *-multimedia:3 UNCLAIMED
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: c.1
       bus info: pci@0000:00:0c.1
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=255 mingnt=4

---

### Post by rebelrex on 2008-11-09
> **kleeman said:**
> I have had this problem a lot. The solution is to ensure that the onboard soundcard is not regarded (by alsa) as the default card. What I do is edit the file

/etc/modprobe.d/alsa-base

at the bottom of this file you will see a whole bunch of lines like

options snd-intel8x0m index=-2

These ensure that certain soundcards are not the default ones
You need to add your similar line here with the correct alsa module (i.e. the snd-intel8x0m of the above sample line). To figure this out open a terminal and type

lsmod | grep snd

Report the out put and I'll tell you what the replacement for snd-intel8x0m needs to be for your system.....

This can also be found by the 

lshw -C sound

command suggested above. Look for the module=XXXXXX

and XXXX is what you need....

I tried this solution once, the problem with it was that it didn't seem work in games..I mean , some games still used the onboard card..
the solution that worked best for me was to add the onboard sound card to the blacklist...the problem is , I am not sure I am doing it correctly, and I think it causes me other problems (like computers freezes)
thats why I want to be sure I am am blacklisting the sound device correctly

Does this solution works good for you in all aplications?

---

### Post by kleeman on 2008-11-09
> **rebelrex said:**
> I tried this solution once, the problem with it was that it didn't seem work in games..I mean , some games still used the onboard card..
the solution that worked best for me was to add the onboard sound card to the blacklist...the problem is , I am not sure I am doing it correctly, and I think it causes me other problems (like computers freezes)
thats why I want to be sure I am am blacklisting the sound device correctly

Does this solution works good for you in all aplications?

Try it and see. BTW the line you need is exactly he same as mine i.e

.options snd-intel8x0 index=-2

I would be surprised if the games did not use the audigy driver i.e soundblaster.

ALL of my apps (games included) are fine.....

---

### Post by rebelrex on 2008-11-09
ok i'll try this again as soon as I'll get home. I really hope this will work..

---

### Post by rebelrex on 2008-11-09
> **kleeman said:**
> Try it and see. BTW the line you need is exactly he same as mine i.e

.options snd-intel8x0 index=-2

I would be surprised if the games did not use the audigy driver i.e soundblaster.

ALL of my apps (games included) are fine.....

ok I tried that now
at first it seemed to work
but then I checked the sound on virtualbox (xp), and its output was still only in the onboard card..

---

### Post by rebelrex on 2008-11-10
Can any1 help me please? I want to disable 1 sound card and I dont sure how to do it!

---

