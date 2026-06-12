---
title: "[SOLVED] 3ddesk problem"
date: 2008-10-08
forum: General Help
---

### Post by prabath_fun on 2008-10-08
Hi,
  I referred following HOW TO: Switch desktops in 3D view! Cool! ([http://ubuntuforums.org/showthread.php?t=100169](http://ubuntuforums.org/showthread.php?t=100169)) thread and installed 3ddesk in my Ubuntu8.04. 
  After I execute 3ddesk command in terminal, I got

Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

Please help me to solve this.
With advanced Thanks,
Prabath

I could not able to post query in above mentioned thread - I am opening this thread.

---

### Post by loomsen on 2008-10-08
It would be kinda helpful for people willing to help you, if you'd give some information about your hardware. Anything else is just guessing in the dark.

But, apart from that, the thread you refer to is nearly 3 years old. And, considering cpu speed increses 100% within 18 months, why don't you simply use compiz? I'm sure you'll find some possibilities to switch desktops you'll like too...
[/offtopic]

NTL, as I said, please post some information about your hardware, for example get compiz-check and post its output.

You can get it by typing:
```

wget http://blogage.de/files/4359/download -O compiz-check && chmod +x compiz-check
```
When downloaded and made executable, run it with:
```
./compiz-check
```
and post its output.

You will get some more help then I think.

---

### Post by prabath_fun on 2008-10-13
> **loomsen said:**
> It would be kinda helpful for people willing to help you, if you'd give some information about your hardware. Anything else is just guessing in the dark..
Please find the hardware details of my desktop
Intel make Motherboard - D102GGC2. 
Some hints about my motherboard:
High Definition Audio Subsystem
The board includes a flexible 6-channel audio subsystem based on a High Definition Audio interface. The audio subsystem features:
• ATI IXP 450 Southbridge
• Realtek ALC883 audio codec
• Impedance sensing capability for jack re-tasking
• S/N (signal-to-noise) ratio of 90 dB
• Microphone input supporting:
&#9135; Stereo microphone
&#9135; Microphone boost

My desktop contains Vista. Through Vista, Ubuntu 8.04 was installed with wubi8.04 using Ubuntu 8.04 Live CD

> **loomsen said:**
> 
But, apart from that, the thread you refer to is nearly 3 years old. And, considering cpu speed increses 100% within 18 months, why don't you simply use compiz? I'm sure you'll find some possibilities to switch desktops you'll like too...
[/offtopic]

NTL, as I said, please post some information about your hardware, for example get compiz-check and post its output.

You can get it by typing:
```

wget http://blogage.de/files/4359/download -O compiz-check && chmod +x compiz-check
```
When downloaded and made executable, run it with:
```
./compiz-check
```
and post its output.

You will get some more help then I think.

---

### Post by prabath_fun on 2008-10-13
> **loomsen said:**
> It would be kinda helpful for people willing to help you, if you'd give some information about your hardware. Anything else is just guessing in the dark..
Please find the hardware details of my desktop
Intel make Motherboard - D102GGC2. 
Some hints about my motherboard:
High Definition Audio Subsystem
The board includes a flexible 6-channel audio subsystem based on a High Definition Audio interface. The audio subsystem features:
&#8226; ATI IXP 450 Southbridge
&#8226; Realtek ALC883 audio codec
&#8226; Impedance sensing capability for jack re-tasking
&#8226; S/N (signal-to-noise) ratio of 90 dB
&#8226; Microphone input supporting:
&#9135; Stereo microphone
&#9135; Microphone boost

My desktop contains Vista. Through Vista, Ubuntu 8.04 was installed with wubi8.04 using Ubuntu 8.04 Live CD

> **loomsen said:**
> 
But, apart from that, the thread you refer to is nearly 3 years old. And, considering cpu speed increses 100% within 18 months, why don't you simply use compiz? I'm sure you'll find some possibilities to switch desktops you'll like too...
[/offtopic]

NTL, as I said, please post some information about your hardware, for example get compiz-check and post its output.

You can get it by typing:
```

wget http://blogage.de/files/4359/download -O compiz-check && chmod +x compiz-check
```
When downloaded and made executable, run it with:
```
./compiz-check
```
and post its output..

./compiz-check

Gathering information about your system...

Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: ATI Technologies Inc RC410 [Radeon Xpress 200]
Driver in use: radeon
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [ OK ]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [ OK ]

as output.


Even, I tried Compiz by enabling Hardware (by installing xorg.fglrx driver). After installation and reboot the PC, I am getting out of range problem. Even I edited /etc/X11/xorg.conf of display subsection for 1024x768 resolution. I got same out of range problem.

> **loomsen said:**
> 
You will get some more help then I think.

Please update me with more tips to get desktop effects.
With advanced Thanks,
[COLOR="DarkOrchid"]Prabath[/COLOR]

---

### Post by prabath_fun on 2008-10-13
HI,
   I got Desktop effects. I modified xorg.conf with 1024x768 instead of 1024x768_60.
With Thanks,
Prabath

---

### Post by prabath_fun on 2008-10-13
HI,
   I got Desktop effects. I modified xorg.conf with 1024x768 instead of 1024x768_60.
With Thanks,
Prabath

---

