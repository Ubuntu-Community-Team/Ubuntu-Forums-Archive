---
title: "Lucid, integrated microphone not working on asus f50z"
date: 2010-07-14
forum: Hardware
---

### Post by louisJ on 2010-07-14
Hi

on asus x50z, does anybody know how to make the integrated microphone work?
I tried the "system test" of ubuntu (10.04), the mic does not respond..
 Mic is not muted in sound preferences.

thanks.

```

$uname -a gives 2.6.32-23-generic

$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: SB [HDA ATI SB], périphérique 0 : ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: SB [HDA ATI SB], périphérique 1 : ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 14 2010 for kernel 2.6.32-23-generic (SMP).

$ lspci -v
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: ASUSTeK Computer Inc. Device 19c3
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fdbf4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

---

### Post by Iowan on 2010-07-16
Moved (by request) to Hardware & Laptops.

---

### Post by louisJ on 2010-07-17
up

---

### Post by lidex on 2010-07-18
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by louisJ on 2010-07-21
Hi lidex

Thank you very much it works! Ubuntu gets the input sound from the mic.

And Skype also does get the input, after I unmuted the FF-MIC channel in alsamixer.

So it is great
Thanks again for your help.

---

### Post by lidex on 2010-07-21
You're welcome. Enjoy!

---

### Post by louisJ on 2010-07-23
Hey Lidex,

I have another problem though.
When I plug the headphones, the sound still outputs by the speakers (in addition to the headphones).
Any idea what to do?

Thanks

---

### Post by lidex on 2010-07-23
Are you using the headphone out or line out. Line out probably won't mute.

Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by louisJ on 2010-08-22
Hi Lidex,

sorry for answering so late.
I tried gnome-alsamixer (and alsamixer too) but I don't find a combination of settings that allows for the sound from the speakers to mute when plugging the headphones. When lowering PCM or Master, both heaphones and speakers volumes go down.
Any idea?

Thanks.

---

### Post by lidex on 2010-08-23
> **louisJ said:**
> Hi Lidex,

sorry for answering so late.
I tried gnome-alsamixer (and alsamixer too) but I don't find a combination of settings that allows for the sound from the speakers to mute when plugging the headphones. When lowering PCM or Master, both heaphones and speakers volumes go down.
Any idea?

Thanks.
Have you tried changing the connector on your sound preferences output tab?

---

### Post by louisJ on 2010-08-24
> **lidex said:**
> Have you tried changing the connector on your sound preferences output tab?
In the output tab of sound preferences, I have only one line (Audio interne Analog Stereo), and it is checked.
I don't know how to change that.

---

### Post by lidex on 2010-08-24
> **louisJ said:**
> In the output tab of sound preferences, I have only one line (Audio interne Analog Stereo), and it is checked.
I don't know how to change that.

Down below that where it says 'Connector'

---

### Post by louisJ on 2010-08-25
Curiously, I don't have the 'connector' line in the output tab...see the screen capture (sorry French language)

---

### Post by lidex on 2010-08-25
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by louisJ on 2010-08-26
OK I went through the link in your signature, and ran ```
ubuntu-bug audio
```.
When I go to launchpad, I already see the bug filed, I guess that this command automatically files it.
Is it the case?

Do you think this would work: [http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

Thank you

---

### Post by lidex on 2010-08-27
What is the launchpad link?

---

