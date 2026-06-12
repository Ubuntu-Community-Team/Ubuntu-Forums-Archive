---
title: "No sound with MSI EX625 Laptop"
date: 2009-06-09
forum: Hardware
---

### Post by Vyresince on 2009-06-09
I have recently installed Ubuntu 9.04 onto my new MSI EX625 laptop (I'm dual-booting with Windows Vista).  Everything seems to be working splendidly except for my sound.  I have gone through the sound trouble-shooting documentation linked to by the Ubuntu site to no avail.  I'm hoping perhaps one of you fine folks can help me get sound working!  I hope it's not the case that my hardware is not supported.  Anyway, below is some information that might be helpful.  If there is anything else that would be helpful, please let me know.  Thanks!

**Version of Ubuntu:** 9.04
**Kernel:**                   2.6.28-11-generic
**Environment:**         GNOME 2.26.1
[B]Audio Devices (from "lspci -v" output):
[/B]
[LIST]
[*]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Micro-Star International Co., Ltd. Device 6740
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fdef8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
[*]06:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
        Subsystem: Micro-Star International Co., Ltd. Device aa38
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at febec000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
[/LIST]
[B]Output of "aplay -l":
[/B][INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[/INDENT]I have provided the information used in the sound trouble-shooting documentation, but if there is any other information that would be helpful, please let me know.  Thanks!

(As a warning, I am a relative novice when it comes to Ubuntu/Linux, so you may want to be rather detailed in any advice/help you give me).

---

### Post by roxann on 2009-07-04
I am having the exact same problem. I just installed xubuntu 9.04 on my msi ex625 and I'm getting no sound whatsoever.
Does anyone know how to fix this?

---

### Post by nahu on 2009-07-22
1. Sorry for my bad english.

2.     * Open /etc/modprobe.d/alsa-base with the following command: 

> sudo nano /etc/modprobe.d/alsa-base

Then paste the following line at the end of the file:

> options snd-hda-intel model=3stack-6ch-dig

    * Reboot

ref: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

3. * In alsamixer turn on the headphone:

   > alsamixer
      
      select the headphone in alsamixer and press M

the subwoofer not work :confused:, but the front speaker yes :o

---

### Post by Sharky_PL on 2009-07-22
> **nahu said:**
> 1. Sorry for my bad english.

2.     * Open /etc/modprobe.d/alsa-base with the following command: 



Then paste the following line at the end of the file:



    * Reboot

ref: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

3. * In alsamixer turn on the headphone:

   
      
      select the headphone in alsamixer and press M

the subwoofer not work :confused:, but the front speaker yes :o





This works :) Although the subwoofer does not, this is right. But it does not matter to be honest, as long as it works at all.

How to make the built-in microphone work?

---

### Post by Vyresince on 2009-07-31
> **nahu said:**
> 1. Sorry for my bad english.

2.     * Open /etc/modprobe.d/alsa-base with the following command: 



Then paste the following line at the end of the file:



    * Reboot

ref: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

3. * In alsamixer turn on the headphone:

   
      
      select the headphone in alsamixer and press M

the subwoofer not work :confused:, but the front speaker yes :o

 The above worked for me!  Thank you so much!

---

### Post by Wavel on 2009-09-18
Nahu i cannot thank you enough for this help.

Have the same lappie and now all is right, even the subwoofer is doing fine ( the surround option activate it ).

Many  thanks.

Oh ,and i think ( obvious when my java skill improve ) doing some software to active the 3 touch buttons from this notebook.

This could really provide a better experience using the system.

---

### Post by aeubz on 2010-01-07
Hi, I tried the command but every time I paste the "options snd-hda-intel model=3stack-6ch-dig" command in the "sudo nano /etc/modprobe.d/alsa-base" and try to exit, it says "There is still a process running in this terminal.  Closing the terminal will kill it."  I restart and the changes are not saved.  How do I deal with this problem?

Edit:  Doing a little surfing I found that you need to do "ctrl +o" to save changes.  Also if anyone is trying "sudo nano /etc/modprobe.d/alsa-base" and theres no commands in the file, you might need to type a .conf at the end.  So try "sudo nano /etc/modprobe.d/alsa-base.conf" and then paste the command.  Worked for me and thanks!

---

