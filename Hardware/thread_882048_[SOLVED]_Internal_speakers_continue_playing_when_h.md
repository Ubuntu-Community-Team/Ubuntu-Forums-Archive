---
title: "[SOLVED] Internal speakers continue playing when headphones"
date: 2008-08-06
forum: Hardware
---

### Post by desideratha on 2008-08-06
I am using Ubuntu Studio on a Sony Vaio Laptop.

Internal speakers continue playing when headphones are connected!
How can I fix that? Any help appreciated

Thanks

---

### Post by desideratha on 2008-08-06
Internal speakers do not mute when using headphones

Any help appreciated

Thanks

---

### Post by phidia on 2008-08-06
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?p=5523006#post5523006") and see if that works for you.

---

### Post by cespinal on 2008-08-06
Search the forums, thst quite common problem so you may find the solution soon

---

### Post by desideratha on 2008-08-13
Still having been able to solve, after searching, installing new alsa drivers and changing al the option on options snd-hda-intel model=MODEL

help please cannot use headphones

---

### Post by Nepherte on 2008-08-13
Did you check this out? [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (if you do have an intel hda sound card of course)
I hope you actually replaced MODEL to fit your model?

---

### Post by desideratha on 2008-08-13
Nepherte.  Yes I did, I install latest drivers, none of the options for my sound card seem to work (options .. etc = model) in the alsa-base file...

any clues 

this is rather frustrating...

thanks

---

### Post by desideratha on 2008-08-13
thansk , I tried it, no luck

---

### Post by Nepherte on 2008-08-13
Next time, use one thread for one problem instead of 2 threads for one (cfr. [http://ubuntuforums.org/showthread.php?t=882061](http://ubuntuforums.org/showthread.php?t=882061))

What is the output of:
```
cat /proc/asound/card0/codec#* | grep Codec
```

What Sony laptop do you have?

Did you try:
```
options snd-hda-intel model=vaio
```

You could also try adding probe_mask=1 or 2:
```
options snd-hda-intel model=vaio probe_mask=1
```

---

### Post by overdrank on 2008-08-13
Hi and desideratha please do not create multiple threads on the same issues as it may cause confusion. 
Threads merged.

---

### Post by desideratha on 2008-08-13
Ok, I'll use one thread next time.

I have a sony vaio vgn-n250

Codec: Realtek ALC262
Codec: Conexant ID 2c06


Thanks

Ps Yes I try options snd-hda-intel model=vaio 

no luck

---

### Post by Nepherte on 2008-08-13
Browsing through this document [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt), looking under ALC262, you have these possible options:
```
810		  fujitsu	Fujitsu Laptop
811		  hp-bpc	HP xw4400/6400/8400/9400 laptops
812		  hp-bpc-d7000	HP BPC D7000
813		  hp-tc-t5735	HP Thin Client T5735
814		  hp-rp5700	HP RP5700
815		  benq		Benq ED8
816		  benq-t31	Benq T31
817		  hippo		Hippo (ATI) with jack detection, Sony UX-90s
818		  hippo_1	Hippo (Benq) with jack detection
819		  sony-assamd	Sony ASSAMD
820		  ultra		Samsung Q1 Ultra Vista model
821		  basic		fixed pin assignment w/o SPDIF
822		  auto		auto-config reading BIOS (default)
```

After googling, another thread of yours popped up: [http://ubuntuforums.org/showthread.php?t=882499](http://ubuntuforums.org/showthread.php?t=882499)
I'd give fujitsu with probe_mask=0 or 1 or 8, auto and basic a try.

---

### Post by desideratha on 2008-08-15
Finally this option works

options snd-hda-intel model=basic probe_mask=1

for my laptop Sony VAIO Vgn-n250

it gives a new set up faders for the headphones, the internal speakers would be control by: front faders (in the volume control alsa mixer)

---

