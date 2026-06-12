---
title: "Ubuntu can't detect my sound card"
date: 2008-10-27
forum: Hardware
---

### Post by KuroYoma on 2008-10-27
I am running ubuntu 8.04 with a custom 2.6.26.1 kernel and can't seem to get Ubuntu to detect my sound card.  Any idea how i might fix this.

---

### Post by teaker1s on 2008-10-27
```
sudo lspci -v
``` find the section with sound card info and from there you can troubleshoot.

also is alsa module installed

---

### Post by KuroYoma on 2008-10-27
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Dell Unknown device 01cb
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 
Enable-
	Capabilities: [70] Express Unknown type IRQ 0
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Unknown (5)

is the output for lspci -v


Yes alsa module is installed

---

### Post by KuroYoma on 2008-10-27
'The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.'

is what i get when i click on my volume button and ...

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

is the error message when i click the test button in sound manager under preferences.

---

### Post by teaker1s on 2008-10-27
at this point I do not know the answer, I would suggest that googling this brings up lots of reports of above output-maybe looking at them will help narrow it down

---

### Post by KuroYoma on 2008-10-27
So useing lspci i see that the hardware is there and seen.  When i use the alsa commands i get this

kuro@kuro-laptop:~$ sudo alsa reload
sudo: unable to resolve host kuro-laptop
[sudo] password for kuro: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kuro/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
kuro@kuro-laptop:~$ sudo /etc/init.d/alsa-utils restart
sudo: unable to resolve host kuro-laptop
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
kuro@kuro-laptop:~$ 


Its acting as if alsa doesn't have the drivers it needs.  Any idea?

Thanks for your help teaker1s

---

### Post by teaker1s on 2008-10-27
normally i use module assistant to install modules. have you tried compiling alsa from alsa project

---

### Post by KuroYoma on 2008-10-27
Actually i am not sure

Do you know the code off hand to run alsa project

---

### Post by teaker1s on 2008-10-27
[http://www.alsa-project.org/]("http://www.alsa-project.org/")


I would 
```
sudo apt-get install module-assistant
```

```
sudo module-assistant
```

I suggest you try using it to compile and install alsa

other than that I don't know what else to suggest

---

