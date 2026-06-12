---
title: "Ubuntu 11.04 64bit, Nvidia Dual Monitor, Creative Sound and Lots of  problems"
date: 2011-07-20
forum: Hardware
---

### Post by vlbaindoor on 2011-07-20
Hi (K)Ubuntu community,

I am a well experienced Linux developer/user and yet I have these problems - can somebody please help me.

My desktop is a ASUS P5Q, Intel Core 2 Quad with 8GB of RAM, Nvidia GeForce 9800GT with two ViewSonic VX2260WM LCD Panels, Creative Labs SB Audigy (rev 04). Dual boot Windows 7 (64bit) and Kubuntu 64bit.

I am running "2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux" kernel. The "lspci -k" command shows - 
"01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)Subsystem: InnoVISION Multimedia Ltd. Device 3040,        Kernel driver in use: nvidia, Kernel modules: nvidia-current, nouveau, nvidiafb"

Problems:

1. I can only use KDE Plasma Desktop. If I try any other version of Gnome or Unity the display is unusable - I would get one black screen on which only the mouse pointer is visible, other LCD screen where icons are displayed but I can not click on any of them - though I can move the mouse over them - unusable.

2. Under KDE everything else seems ok but sound system seems to start correctly and then deteriorates over time and after a while gets too noisy, full of echo and can not be used.

3. I have a Canon Pixma MP560 printer and I had lots of problems installing the drivers.  Though I have now managed to get the printer working - it has not been a good experience to get it working.

The same system has no problems at all with Windows 7, 64bit.

Any help would be appreciated. Thanks

---

### Post by Enkindlers on 2011-07-20
My system is very similar to yours and it works, but I've installed 32 bit system. I didn't try to install peripherals yet, but I've tried so hard to install my sound card (a X-FI Xtreme Audio) and I can't figure out how to make it work. The card is detected by OS to be CA 0106 and after a lot of research I was able to have all my speakers working in the sound preference speaker testing, but I am unable to listen music in 5.1 mode with the music player. What should I do?

---

### Post by vlbaindoor on 2011-07-21
> **Enkindlers said:**
> My system is very similar to yours and it works, but I've installed 32 bit system. I didn't try to install peripherals yet, but I've tried so hard to install my sound card (a X-FI Xtreme Audio) and I can't figure out how to make it work. The card is detected by OS to be CA 0106 and after a lot of research I was able to have all my speakers working in the sound preference speaker testing, but I am unable to listen music in 5.1 mode with the music player. What should I do?

32bit system is quite different from 64bit - as you already know - but I find this reluctance on the part of industry to fully take up 64bit is a sad fact.

I have now installed UbuntuSudio 64 on the same system after formatting the '/' partition - for your information I have a separate '/home' partition on a separate hard disk itself - so my data is safe. 

UbuntuStudio64 seems much better - with little bit of tweaking both the LCD screens are working properly. Sound seems ok - so far - in fact as I type this message I am using Audacity to capture and play music from my old cassette player. So far so good - touch wood.

I had to go into a command prompt using Konsole and ran 'alsamixer' and I had to make sure that the inputs (for recording) and the outputs (playing) were not muted. I found that in particular the LineIn-3 inputs for both recording and playing were set to zero by default and I had to set them to 100%.

I understand that in some (older) Ubuntu versions one needs to tweak, modify and configure Pulse and Alsa and all that - but not with the UbuntuStudio64 and the hardware setup I have.

I am yet to install the printer - but now I want to convert all these cassette tapes to MP3s - so printer configuration would have to wait.

---

### Post by rfbeck on 2011-07-22
Enkindlers,

I used to use one of these X Fi cards. The only solution available at the time was to navigate Creative's drivers and find the lone Linux driver. It worked for my X Fi card and was good for both 32bit and 64 bit Linux installation.. Although I don't I know how its holding up now.

You can find the driver at:

[http://opensource.creative.com/soundcard.html]("http://opensource.creative.com/soundcard.html")
______
Robert



> **Enkindlers said:**
> My system is very similar to yours and it works, but I've installed 32 bit system. I didn't try to install peripherals yet, but I've tried so hard to install my sound card (a X-FI Xtreme Audio) and I can't figure out how to make it work. The card is detected by OS to be CA 0106 and after a lot of research I was able to have all my speakers working in the sound preference speaker testing, but I am unable to listen music in 5.1 mode with the music player. What should I do?

---

### Post by vlbaindoor on 2011-07-22
The reason why the standard 64bit Kubuntu/Ubuntu failed while the UbuntuStudio 64 works may be down to two reasons in my view:

1. The studio version uses a bespoke kernel with Real Time extensions.  The documentation says "Real Time Kernel - Ubuntu Studio uses the Ingo Molnar PREEMPT patched real-time kernel (for more information about the real-time kernel, take a look at the RTWiki FAQ). This helps to reduce the amount of latency, which is extremely beneficial for audio work. The low levels of latency that can be achieved in Linux with the real-time kernel can also surpass those available under Windows and Mac."

Though strangely on my system "uname -a" command shows this:
"Linux AsusP5Q 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux"

No sign of any Real Time credentials - or am I missing something there?

2. The Ubuntu Studio 64bit 11.04 seems to be using the good old Gnome - in other words I did not see any sign of the dreaded 'Unity'.

Here is the 'Real Time' proof (pun intended) - the same machine while using Windows 7, 64bit and Audacity has problems capturing audio from the Line-in of the sound card - but Ubuntu Studio 64bit seems fine so far - touch wood.

---

### Post by vlbaindoor on 2011-07-22
Sorry, my previous message said that I did not see any signs of Unity - I am wrong.

The login screen does have 'Ubuntu' and 'Ubuntu Classic' options for desktop environments - when I select 'Ubuntu'- it does come back with "you do not have the hardware to run 'Unity' running the Classic interface instead'

This issue seems to do with multiple screens and Unity being incompatible - in any case I have greater success with UbuntuStudio than Kubuntu/Ubuntu.

---

