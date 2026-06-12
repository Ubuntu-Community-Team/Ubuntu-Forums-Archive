---
title: "Which one of these two?"
date: 2011-01-20
forum: Hardware
---

### Post by Edoardo_P on 2011-01-20
Hello,

Just... Which one? :p

The only thing that seems to change is the graphic unit:

**Asus 1015PEM** - Intel® GMA 3150

**Asus 1015PN** - NVIDIA ION2 N11M-PT1 512MB VRAM
(will the HDMI out work?)

Thank you very much

---

### Post by Edoardo_P on 2011-01-21
bump

---

### Post by hsoulen on 2011-01-21
> **Edoardo_P said:**
> Hello,

Just... Which one? :p

The only thing that seems to change is the graphic unit:

**Asus 1015PEM** - Intel® GMA 3150

**Asus 1015PN** - NVIDIA ION2 N11M-PT1 512MB VRAM
(will the HDMI out work?)

Thank you very much

The ION2 for sure... You'll give up a bit of battery (Linux is still working on dynamic graphics switching so you will most likely be running ION full time) but it's worth it for 720p video and a bit of gaming.

Either way you don't necessarily want the netbook interface as it is really meant for the smaller 9" screens (1024x600) and the netbook you are looking at runs 1366x768 and the regular desktop works very well.

I use an Asus 1201n with the original ION and it rocks.

Edit... Yes on the HDMI. If you use the binary driver from NVIDIA and the control panel it works very well, just remember you need to also use the HDMI sound (ALSA control panel) when you hook it up.

My two cents, worth one cent.

Hank

---

### Post by Edoardo_P on 2011-01-21
> **hsoulen said:**
> 
Edit... Yes on the HDMI. If you use the binary driver from NVIDIA and the control panel it works very well, just remember you need to also use the HDMI sound (ALSA control panel) when you hook it up.

My two cents, worth one cent.

Hank

Wait: what does the thing of the ALSA drivers mean? 
Will I be able to play music while hooking an external monitor by HDMI?

---

### Post by hsoulen on 2011-01-24
> **Edoardo_P said:**
> Wait: what does the thing of the ALSA drivers mean? 
Will I be able to play music while hooking an external monitor by HDMI?

Hi Edoardo,

Sorry for the confusion. What I meant was that when you use HDMI to connect to a TV you will also need to tell the OS to use the HDMI for audio as well, simply click on the volume icon on the gnome-panel at the top of the screen (default is on top) and select "Sound Preferences" then select the "Hardware" tab and click the "Profile" dropdown and select "Digital Stereo (HDMI) Output" for just HDMI or "Digital Stereo (HDMI) Output + Analog Stereo Output" if you want sound from both the TV and the computer speakers.

Cheers,

Hank

---

