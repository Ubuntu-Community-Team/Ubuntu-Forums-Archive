---
title: "Nvidia GeForce 7000m RAM usage"
date: 2009-06-04
forum: Hardware
---

### Post by ugriffin on 2009-06-04
Hello. I've got an Acer lappy with 1 GB of RAM, a single core 2.2GHZ processor, and an Nvidia GeForce 7000m with an NForce 610m (I believe the second is the motherboard. I'm quite sure, but I won't research to prove it-yet.). Anyways, since my lappy isn't what you would call beauty-built, considering it has a single core processor and my Video Card eats up 256MB of my RAM, I tweaked it so that it ate only 128MB, enough to run Aero on Windows 7 and freeing up a portion of my RAM. Kind of curious to see how my NVIDIA was stacking up, I opened my NVIDIA X Server settings, and to my dismay, it says I apparently have 512MB of memory on my video card. This can't be... last time I checked, the card was low end and HAD to drain from my RAM...  what's wrong? Is the driver stupid, or what is happening? Or I just am a terrible researcher?

I need this info so...

a) I can reduce the card's usage to a mere 32mb... leaving the suspected "dedicated memory" to handle the card.

b) That would increase my RAM usage... very handy, especially considering I still have Vista installed.



Ok... can someone please explain this oddity?

Thanks in advance.

---

### Post by Steelmourne on 2009-06-04
Does your card have a "Powermizer" tab in the X Server settings under GPU 0? This automatically chooses the right performance level depending what you are doing at the time. However, that card has no onboard (dedicated) memory according to this:

[http://www.notebookcheck.net/NVIDIA-GeForce-7000M.8842.0.html](http://www.notebookcheck.net/NVIDIA-GeForce-7000M.8842.0.html)

so the Powermizer settings might take 512MB just for the videocard. How did you tweak the settings on 7 or Vista?

---

### Post by ugriffin on 2009-06-04
I set up the Video card usage on the BIOS... it reported that there were about 875 MB free on the RAM usage. Using free -m also reports similar stats. Unless there's a hidden extra gig in my system, which for some reason doesn't show up ANYWHERE, I can't undestand how it would eat up 512 megs.

Here's the output of GPU 0 on Nvidia X server settings.

```

Graphics Processor: Nvidia GeForce 7000M/ nForce 610M
VBIOS Version: 05.67.32.14.08
Memory: 512 MB.
Bus Type: Integrated
Bus ID: 0:18:0
IRQ: 17
X Screens: Screen 0
Display Devices: AUO (DFP-0)

```

Powermizer settings (apparently it only handles clock speeds).

```

Adaptive Clocking: Enabled.
GPU Clock: 350 MHZ
Memory Clock:666 MHZ
Power Source: AC
Performance Level: 2
Performance Mode: Maximum Performance.

```

---

### Post by Steelmourne on 2009-06-05
It seems that since the card is integrated it takes as much memory as its wants. You could try to manually re-install drivers. That chip is supported.

---

### Post by ugriffin on 2009-06-05
I manually installed the drivers. I downloaded the script from the Nvidia website, if that's what you mean. And I'm still kinda confused... it eats up 512 mb of ram like a normal application would? AND it steals from the RAM too? Or how would this work.

---

### Post by virvet on 2009-07-21
Just to add some info: i have a GeForce 8400M GS ([http://www.notebookcheck.net/NVidia-GeForce-8400M-GS.3709.0.html](http://www.notebookcheck.net/NVidia-GeForce-8400M-GS.3709.0.html)) and Nvidia X Server Settings shows 512MB of video memory.
It's been a nightmare to insall nvidia drivers here, since ubuntu 8.04.

---

