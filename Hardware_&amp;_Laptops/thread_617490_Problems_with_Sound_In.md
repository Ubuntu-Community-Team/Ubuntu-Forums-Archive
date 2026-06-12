---
title: "Problems with Sound In"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by kirtimaan on 2007-11-19
Hello,

I have a Compaq Persario notebook which have an ATI sound card.  Alsamixer shows following information : 

```

Card: ATI IXP                                                                                                             &#9474;
Chip: Conexant id 30

```

In Device Manager, its labeld as IXP SB400 AC'97 Audio Controller. The problem which I am facing is that sound in doesn't work. It worked properly under Windows with the same mic and same notebook. I have no problem with Sound Out and can hear the sound output under Ubuntu. Only sound in (recording from Mic) doesn't work.

I have tried the Sound Recorder, Audacity and different settings in aslamixer and volume control applet, but none worked. 

In terminal when I run alsamixer and press F4 to go to recording mode view, it shows only IEC958 P and Capture device active and Line, CD, Mic are not active and neither I can activate those.

Below is information from my /proc directory : 

```

**cards**

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with unknown codec at 0xc0003400, irq 16
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xc0003800, irq 16

**devices**

  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio playback
  5: [ 1- 0]: digital audio capture
  6: [ 1]   : control
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control

**modules**
 0 snd_atiixp
 1 snd_atiixp_modem

**pcm**
01-00: ATI IXP MC97 : ATI IXP MC97 : playback 1 : capture 1
00-00: ATI IXP AC97 : ATI IXP AC97 : playback 1 : capture 1

**timers**
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P1-0-0: PCM playback 1-0-0 : SLAVE
P1-0-1: PCM capture 1-0-1 : SLAVE

**version**

advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).


```

Please have a look into this and let me know if there is any thing which I can do to start my mic under Ubuntu. I am trying to use Skype and can't make calls unless I have mic setup correctly.

Thanks, Kirtimaan

---

