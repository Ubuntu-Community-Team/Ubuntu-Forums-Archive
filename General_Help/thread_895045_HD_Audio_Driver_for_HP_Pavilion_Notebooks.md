---
title: "HD Audio Driver for HP Pavilion Notebooks?"
date: 2008-08-19
forum: General Help
---

### Post by eival on 2008-08-19
i recently reinstalled ubuntu an i dont remember where to get that driver. or if i need to type something in the terminal to activate it.

it would be nVidia chipset, but ive already installed the video drivers and the 3rd party drivers, but my media controlls on the laptop arent working, so i know i forgot something

:confused:

---

### Post by xeth_delta on 2008-08-19
please post the output of the command
```
lshw -C sound
```

[EDIT] Here is a link with more information about debugging sound problems in Ubuntu: [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

---

### Post by eival on 2008-08-19
PCI (sysfs)  
  *-multimedia            
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

---

### Post by eival on 2008-08-19
its working now:lolflag:

did that code activate it?

cause the mute button on my laptop's media control wasnt working until just now

either way, thanks. its working.:popcorn:

---

### Post by xeth_delta on 2008-08-19
> **eival said:**
> its working now:lolflag:

did that code activate it?

cause the mute button on my laptop's media control wasnt working until just now

either way, thanks. its working.:popcorn:

No, the command I gave you was simply supposed to tell us what sound chip is found in your computer.

My guess would be that the sound system was restarted (either by reboot or alsa services restart) and the modules/drivers reloaded.

Anyway, glad to hear it's working now.

---

### Post by tonyblue on 2008-11-29
hey everybody,
i have a notebook pavilion dv9260us. i've installed ubuntu 4 months ago, and since then i have some problems with the sound. in comparison with my vista ultimate 64 bit OS, in ubuntu the volume is 5-10 times lower. when i set the volume max i can only hear lower sound, let's just say 30% of the volume of the sound card using windows vista. i've tried some commands after searching google, but they had the same result.
CAN ANYBODY SOLVE MY PROBLEM?
THANKS IN ADV
Toni

---

### Post by tonyblue on 2008-11-29
thax for the ones who was replying this thred. i raised my volume using alsamixer.
toni

---

