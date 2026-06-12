---
title: "Soundblaster Live! card not detected or not working"
date: 2008-11-17
forum: Hardware
---

### Post by tee2 on 2008-11-17
I just put it in an old computer for my brother because his onboard sound wasn't working so I thought I'd try this SoundBlaster Live card. Turns out still no sound. I went into synaptic and reinstalled alsa and some other sound related packages hoping that would get things go to no avail. Please help so my brother won't have an excuse to use my computer. :)

This is Xubuntu 8.10 btw.

Thanks.

---

### Post by tee2 on 2008-11-18
bump

Anyone have any ideas?

---

### Post by tee2 on 2008-11-19
bump

Any ideas??

---

### Post by tee2 on 2008-11-20
Can someone please help??

---

### Post by tee2 on 2008-11-21
Wow.  Can no one help?  :(

---

### Post by cariboo on 2008-11-22
Could you paste the output of:

```
sudo lshw -C sound
```

This will show the if the driver is loaded.

You may want to try double-clicking the sound icon in the upper panel and make sure the Master and PCM controls are turned up all the way.

Jim

---

### Post by tee2 on 2008-11-22
> **cariboo907 said:**
> Could you paste the output of:

```
sudo lshw -C sound
```

This will show the if the driver is loaded.

You may want to try double-clicking the sound icon in the upper panel and make sure the Master and PCM controls are turned up all the way.

Jim

```
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=20 mingnt=2

```

When I double click on the sound icon no controls are displayed by the way. The program opens but there are no sliders.

---

### Post by tee2 on 2008-11-24
bump

---

### Post by tee2 on 2008-11-27
bump

---

### Post by XaeroDegreaz on 2008-11-28
I'm not an expert on Linux, but your output shows that the sound card "UNCLAIMED" which probably means that the system has detected it, but has not assigned the hardware to use the drivers.

I'm having a problem getting my SB Live card to work as well, but my card doesn't say unclaimed.

Try installing all of the alsa drivers. You can search for them in the Synaptic Package Manager.

It's worked for me before, but for some reason it isn't working for me this time (Just switched from Kubuntu to Xubuntu and trying to rmember how I did it before >.<)

Good luck.

---

