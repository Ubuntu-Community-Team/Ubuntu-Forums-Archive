---
title: "no sound after suspend/resume,  gateway M6878"
date: 2009-11-13
forum: Hardware
---

### Post by gertjan_hofman on 2009-11-13
9.10 is my first upgrade from a very successful  8.04 install on this laptop. Everything still works, except I have no sounds any more after a suspend/resume, which makes suspend rather useless.  The following works:

log out.  Log in as root,  do alsa force-reload

The card is a:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 0380
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22


I dont mind doing a alsa force-reload after suspend if I can do it without logging out.  However, the problem is that it is unable to kill the pulseaudio-server and so the reload is not succesful. How do I kill the pulseaudio server ?   pulseaudio -k just causes an immediate restart. Does any one know which (gnome ?) daemon is responsible for the restarting of pulseaudio ?  I once had success by killing the volume control applet, then doing alsa force-reload but I couldnt repeat this


The other thing I have read is to specify the exact model sound card number in 
/etc/modprobe.d/alsa-base.conf 

However, none of the models listed in HD-Audio.txt seem to corrospond to this laptop.  Does any one know how to find the exact model ?


Any hints are much appreciated.

Thanks

Gertjan

---

### Post by thunderstick on 2009-11-14
Same problem here.

---

### Post by WingNa on 2009-11-15
@GertJan: you are mentioning Alsa and Pulse at the same time. Must make a choice.

Try to get rid of Pulseaudio (sadly) in the first place. And switch to (good-ol' alsa) Esound. This will get you moving again on Karmic for now (did that with me on Karmic, using snd-hda-intel). Since Pulse is the way forward, give it a try next upgrade.

$ sudo apt-get remove pulseaudio
$ sudo apt-get install esound
# make sure to check any muted channels using the graphical mixer, or alsa-mixer. 

After suspend/ resume, sound comes back like a charm.

This is a bit of a sad story, but will get you moving alright.

Reversely remove Esound and install Pulseaudio will get you back to pulse again.

---

### Post by gertjan_hofman on 2009-11-15
Hi WIngNa,

Thanks for the tips. I am afraid of hopelessly getting things to an irrepairable state (sound-wise) but I will give it a shot. I can always re-install Karmic, the 8.04 is still on this laptop.
I have to admit, I am also confused about the alsa-pulseaudio duality. Lots of 'solutions' to sound problems in systems with pulseaudio are still referring to restarting alsa.  Presumably it's just a matter of using the scripts to reload the kernel drivers.

Shouldnt this work:
  /usr/bin/pactl suspend-sink 1
then reload the drivers and reset the sink ?

See forexample: [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/bef8342095751302?pli=1](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/bef8342095751302?pli=1)


Thanks

Gertjan

---

### Post by gertjan_hofman on 2009-11-17
trying to apt-get remove pulseaudio wants to remove the entire ubuntu-desktop.  Any way to avoid this dependency issue ?

Thanks

Gertjan

---

### Post by VirusCollector on 2009-12-07
Gateway m-6846 here, please bump. Same thing happens to me... so annoying.

---

### Post by gertjan_hofman on 2009-12-12
I tried to suggested solution (getting rid of pulse audio) but it didnt fix the suspend issue. Also, it remove the gnome volume manager and it wasnt immediately obvious how to get it back.
My guess is the best way is still to convince pulse audio to let go of /dev/audio (or whatever it is locking) and then doing alsa force-reload.

I gave up for now. Hibernate works fine and it takes about 50 s. I can live with that for now. GIven the stat of the battery, at least I have some juice left if I leave it for a day or two.

Cheers

G

---

### Post by bartman on 2009-12-30
Hi!

I'm experiencing the same issue on my slightly older laptop with ICH6.
```
$ lspci -vvnn|grep -i audio
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
```

The problem is that after a suspend (which is more useful to me than hibernate) the built-in speakers do not work but the headphone jack IS active. Might alsa sense the jack plugged in all the time?

The mentioned recipe for getting it to work works for me - log out, log in, # alsa force-reload.

I will file a bug report!

---

