---
title: "Microphone doesn't work - SigmaTel High Def Audio"
date: 2009-08-15
forum: Hardware
---

### Post by eakergd on 2009-08-15
Everything seems to be working with my audio, except for the microphone.  This is annoying, because I like to use skype pretty regularly.  I have a Sony Vaio laptop (AR150G).  I am using the standard install of Ubuntu 9.04, and the only extra driver I loaded is for the video.  Can anyone help me get the microphone working.  Here is the chipset info:

dad@dad-laptop:~$ sudo lshw -C multimedia
[sudo] password for dad: 
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia UNCLAIMED
       description: Multimedia controller
       product: Fujitsu Limited.
       vendor: Fujitsu Limited.
       physical id: 4
       bus info: pci@0000:0a:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=64 mingnt=16


Thanks in advance.

Gary

---

### Post by nixscripter on 2009-08-16
The first thing to check is mixer levels. Open a terminal and run ```
aslamixer
``` to look at them. Press **tab** to swich to input devices. The microphone should show up. Use **M** to unmute (if it shows MM at the bottom of the meter), and the arrow keys to adjust the volume.

---

### Post by Green9090 on 2009-08-16
I'm going to jack this thread because my microphone also doesn't work. I type aslamixer in the terminal and it doesn't recognize the command :confused:

---

### Post by nixscripter on 2009-08-17
Make sure you have the **alsa-utils** package installed (in Synaptic package manager).

---

### Post by Yellow Pasque on 2009-08-17
The command (without the typo ;) ) is:
```
alsamixer
```

---

