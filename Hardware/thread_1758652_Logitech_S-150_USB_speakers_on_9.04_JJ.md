---
title: "Logitech S-150 USB speakers on 9.04 JJ"
date: 2011-05-14
forum: Hardware
---

### Post by Deciple X2 on 2011-05-14
Hi everyone
 

I've done a search in this form for this issue and saw one post from 2009 with no response but I'll try my self. 

I've tried a lot of different stuff to try and get these speakers to work. For whatever reason I can't get sound to come out of them. When I press the volume buttons the speakers the screen shows me that the volume is going up, down and muted. 

Does anyone know how to get these speakers to work on 9.04 if it helps i'm using a Dell Dimension 2400. 

Also I new to linux and don't know a lot so I'll need good detailed explanations.

Thanks

---

### Post by kostkon on 2011-05-14
You are using an old and unsupported version of Ubuntu.

Anyway, what options are there in your sound preferences?

---

### Post by Deciple X2 on 2011-05-15
> **kostkon said:**
> You are using an old and unsupported version of Ubuntu.

Anyway, what options are there in your sound preferences?


My options are 

Autodetect
Intel 82801DB-ICH4 WITH AD1981B INTEL 82801DB-ICH4 - IEC958 (ALSA)
Intel 82801DB-ICH4 WITH AD1981B INTEL 82801DB-ICH4 - (ALSA)
USB AUDIO USB AUDIO (ALSA)
Intel 82801DB-ICH4 WITH AD1981B INTEL 82801DB-ICH4 - (OSS)
Intel 82801DB-ICH4 WITH AD1981B INTEL 82801DB-ICH4 - (OSS)
Intel 82801DB-ICH4 WITH AD1981B INTEL 82801DB-ICH4 - (OSS)
USB AUDIO USB AUDIO (OSS)
USB AUDIO USB AUDIO (OSS)
ALSA - ADVANCED LINUX SOUND ARCHITECTURE
OSS - OPEN SOUND SYSTEM
PULSEAUDIO SOUND SERVER

Those are my options for Sound Events, Music and movies, and the sound playback section of Audio Conferencing. 

I guess if you think it'll be the best thing I can upgrade to 10.4 I had done that before but after a while 10.4 got stuck at the boot screen for some reason.

---

### Post by kostkon on 2011-05-15
I Would recommend you to set your sound device in your sound prefs  to autodetect and then install the PulseAudio Volume Control utility (its package name is pavucontrol) and set your usb speakers as the default output device from there.

---

### Post by Deciple X2 on 2011-05-16
Thanks for the advice that got my speakers working! now if only I can figure out how to mark this thread solved...

---

