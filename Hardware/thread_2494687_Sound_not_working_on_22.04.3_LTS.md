---
title: "Sound not working on 22.04.3 LTS"
date: 2024-01-23
forum: Hardware
---

### Post by madscientist032 on 2024-01-23
Hello forums & support users.

I come to you today as I do not have sound from the rear output of my motherboard, however I do see the device listed in lshw & lspci.

I've verified that my speakres are plugged into the correct 3.5 mm jack on the rear of my x570s motherboard AND I can confirm that the 2.1 speakers I am trying to utilize via 3.5 mm jack function on their own perfectly fine as I tested with my phone.

This means it's more likely it's a *nix issue separate from the speakers themselves. I suspect it's how the OS is talking to the integrated audio solution but I'm not really quite sure. 

I've been dealing with this since November 2023. I've never had audio issues before with my workstation, and to be honest I've just been too lazy to post & ask about it as sometimes issues like these solve themselves in time. But I'm tired of wearing headphones all the time, so I am reaching out for help.

I looked at my system with pauvcontrol and alsamixer and - to tell you the truth - it looks like everything's detected, so I'm honestly scratching my head as to why I cant get audio out from the rear 3.5 jack. 

Here are some additional details: 

```
madsci@bosdsk2ubncto:~$ sudo lspci -v | grep -A7 -i audio
[sudo] password for madsci: 
0d:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Navi 21 HDMI Audio [Radeon RX 6800/6800 XT / 6900 XT]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Navi 21 HDMI Audio [Radeon RX 6800/6800 XT / 6900 XT]
    Flags: bus master, fast devsel, latency 0, IRQ 194, IOMMU group 31
    Memory at fc924000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
--
10:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller
    Subsystem: Gigabyte Technology Co., Ltd Starship/Matisse HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 196, IOMMU group 39
    Memory at fcd00000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [64] Express Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>

```

Screenshots of pavucontrol + alsamixer. 
Note, for pavucontrol, it's clear there is audio being generated as I see it on the meter, but I don't hear it from the speakers. So weird!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293328&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293329&stc=1[/IMG]

---

### Post by johnmne on 2024-01-23
According to the image that you attached, it seems that the audio output is sent via the HDMI/DP cable.
Instead, you should choose Line Out. 
See example in the image:
[https://imgur.com/a/oxEK53u](https://imgur.com/a/oxEK53u)

---

### Post by madscientist032 on 2024-01-23
Hello. It's not set to HDMI audio, though as an aside, I was using that as a break-fix as my monitor has built in cruddy speakers (better than nothing).

Here's a screenshot of my sound settings panel. I still don't have audio. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293330&stc=1[/IMG]

---

### Post by him610 on 2024-01-24
Don't know if this will help or not. 
In addition to advice in #2, You should consider raising the level into the upper middle band of Line and Line Boost in Alsamixer. 
Try to stay out of the red bands on the remaining Alsamixer settings; instead, adjust it to mid-range setting.
Can you get any sound out through your front 3.5mm audio connection to your wired headphones?

---

### Post by madscientist032 on 2024-01-27
Hello - sorry for delayed response, things got busy around here and my PC was on the backburner.

I changed the volume out as per your recommendation, still no sound from rear audio jack.

I do have front-panel audio though but it's very poor, almost like it's mono. I am not sure if that's the fault of the jack, the cord, or the headset.

Do you have any other suggestions on how to restore the audio (without resorting to a fresh re-install of ubuntu?)

---

### Post by him610 on 2024-01-28
Make sure socket you are using is the one with the lime green (Line Out) circle around it.

---

### Post by madscientist032 on 2024-01-29
> **him610 said:**
> Make sure socket you are using is the one with the lime green (Line Out) circle around it.

It's 100% in the correct port.

Also, new development - I found out that the same issue persists in my Windows installation (I have a dual-boot configuration).

In windows, I was able to use the realtek control panel to remap the line-in to a different jack which helps but its not ideal as I spend 95% of my time in Ubuntu. 

I don't know how to do that in Linux so I guess I'll play around with alsamixer & other control utilities to see how far I get, or worse-case-scenario dig out an old USB soundcard and use that instead.

---

### Post by Yellow Pasque on 2024-01-29
Maybe hdajackretask is what  you're looking for.
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

---

### Post by him610 on 2024-01-30
> I do have front-panel audio though but it's very poor, almost like it's mono.
Even if it is distorted, it indicates you do have audio. Try plugging your speakers into the front audio output socket to hear what happens..

---

