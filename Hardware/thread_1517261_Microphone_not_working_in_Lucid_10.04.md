---
title: "Microphone not working in Lucid 10.04"
date: 2010-06-24
forum: Hardware
---

### Post by LeapingLlama on 2010-06-24
I recently bought a lenovo g555 laptop and installed ubuntu. Everything seems to work fine except for the fact that my internal microphone does not pick up any sound. I have an HDA ATI SB sound card with a Conexant 5069 chip. I already looked at the help thread for my sound card, but my chip was not listed. I also do not think it is a driver issue, as my sound works fine and my microphone is recognized. It simply will not pick up sound. I have also made sure that the input volume is not muted. I am running Lucid Lynx 10.04.

If anyone could help me out, I would tremendously appreciate it.
Thanks!

EDIT: My microphone was working as of last night. After I rebooted, it no longer worked. However, it only worked last night, and did not work before then.

---

### Post by VH-BIL on 2010-06-24
The microphone in Lucid does not loop back to the speakers. To hear the microphone try:
```
pactl load-module module-loopback
```
This can have bad latency so I use Jack for audio.

---

### Post by LeapingLlama on 2010-06-24
> **VH-BIL said:**
> The microphone in Lucid does not loop back to the speakers. To hear the microphone try:
```
pactl load-module module-loopback
```
This can have bad latency so I use Jack for audio.

Well, the problem is not that I can't hear my mic looped to my speakers, it's that my microphone is not receiving input. When I go to the input tab in sound preferences and speak, the input level meter does not move at all. It did move when my microphone worked briefly last night, though.

---

### Post by VH-BIL on 2010-06-24
And you have tried all the connector options?

---

### Post by LeapingLlama on 2010-06-24
Pardon my ignorance, but what are the connector options?

EDIT: Nvm. I don't have any connector options.

---

### Post by VH-BIL on 2010-06-24
System > Preferences > Sound > "Input Tab"
There is a connector option drop down list in that tab.

---

### Post by LeapingLlama on 2010-06-24
Mmkay I don't have any connector options, only "choose a device for sound input" and only one mic is listed there.

---

### Post by VH-BIL on 2010-06-24
> **LeapingLlama said:**
> Mmkay I don't have any connector options, only "choose a device for sound input" and only one mic is listed there.

You had me confused for a second. I thought you had no connector options which would mean the microphone input is not being detected but only having one is still an option :p

In the hardware tab is there only one in there?

---

### Post by LeapingLlama on 2010-06-24
Yes, there is only one device there

---

### Post by VH-BIL on 2010-06-24
Are you sure the hardware (microphone etc.) is still working?

---

### Post by LeapingLlama on 2010-06-24
Yeah, I just booted into Windows and tried using skype and everything worked fine.

---

### Post by VH-BIL on 2010-06-24
And after a reboot of Ubuntu is it still not working?
Im at a loss now im sorry.

---

### Post by LeapingLlama on 2010-06-24
Well thanks for your time, I appreciate it. I guess I'll just do voice chats in windows.

---

### Post by VH-BIL on 2010-06-24
Don't give up, someone will have the answer.

---

### Post by lidex on 2010-06-25
You may want to try the linuxant drivers. Download and install the correct deb from here:
[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

---

### Post by LeapingLlama on 2010-07-03
I found a solution! I thought I never would, but I was wrong. I upgraded ALSA using the script in lidex's sig, but my mic still didn't work. Certain changes that happened in my system were exactly the same as another person, and lidex recommended they add some lines to alsa-base.conf, so I did the same and my mic is now functional even after multiple reboots. The original post is as follows:
> **lidex said:**
> *saiganeshb* Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.
I am so happy right now, I could explode. Thanks lidex!

---

