---
title: "Sound on Lenovo Legion s7"
date: 2023-08-28
forum: Hardware
---

### Post by rwilley on 2023-08-28
Hello Everyone,

I have recently switched over to Ubuntu on my Lenovo Legion S7, aside from a few hiccups I was able to solve by googling questions everything has gone quite well and I am very impressed at the giant performance upgrade I have experienced since getting rid of Windows 11. The only problem so far I have not been able to solve is my on board sound. I get no sound from my speakers at all. When I go into my sound settings the only option I have for output is Speaker - Family 17th/19th HD Audio Controller. My volume is up both in my sound settings and on YouTube. I have ensured I am not muted. After trying to search around for an answer I have remove PulseAudio (since reinstalled since that didn't work) and used the terminal audio app to make sure my levels were correct. Bluetooth headphones work fine, and for the most part that will suffice but I would like to have my speakers working as well. I have looked through devices and it does recognize my speakers. One last thing I have noticed is that in my sound settings window, next to the word Output at the top there is a small bar that shows when sound is coming through. That is lighting up and showing sound, but nothing is coming out of my built-in speakers. Thank you for any suggestions you might have.

Sincerely,
Rob

---

### Post by #&amp;thj^% on 2023-08-28
Here is an active Lenovo Audio thread: [https://forums.lenovo.com/t5/Ubuntu/Ubuntu-and-legion-pro-7-16IRX8H-audio-issues/m-p/5210709](https://forums.lenovo.com/t5/Ubuntu/Ubuntu-and-legion-pro-7-16IRX8H-audio-issues/m-p/5210709)
I've not solved it myself yet, after a half dozen kernel patches still nothing.
I'll keep mine for another year or so:
```
inxi -FAz
System:
  Kernel: 6.2.0-31-generic arch: x86_64 bits: 64 Desktop: Xfce v: 4.18.1
    Distro: Linux Lite 6.4 LTS
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN37WW date: 04/14/2022
Audio:
  Device-1: NVIDIA driver: snd_hda_intel
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound API: ALSA v: k6.2.0-31-generic running: yes
  Sound Server-1: PulseAudio v: 16.1 running: yes
  Sound Server-2: PipeWire v: 0.3.65 running: yes

```
```
*pactl list sources | grep Simultaneous
	Description: Monitor Source of Simultaneous output to UOEOS Laptop Dock Analog Stereo, Family 17h/19h HD
 Audio Controller Analog Stereo, SRS-XB22
		device.description = "Monitor Source of Simultaneous output to UOEOS Laptop Dock Analog Stereo, Family 17h/19h HD Audio Controller Analog Stereo, SRS-XB22"

```
I've used kernel 5.15 to 6.4 on your machine with no luck.
Might just have to wait it out for a fix to come in.

---

### Post by pt-pepe78 on 2024-01-10
I can confirm the same. On Lenovo Legion Pro 7 16ARX8H, with BIOS switched only to NVIDIA GPU (no hybrid), I can't play audio on speakers, only through headphones. I also tested daily build of Ubuntu today with kernel 6.6, but still same issue appears, which seems like this might not be fixed for a while? [speakers work just fine on Windows 11]

When I go to sound settings I see output device "Speakers - Family 17h/19h HD Audio Controller".

---

### Post by pt-pepe78 on 2024-01-18
Even with latest Manjaro and kernel 6.6.10 (tested today) on [COLOR=#000000]Lenovo Legion Pro 7 16ARX8H[/COLOR], the situation with the speaker is the same (unfortunately). Speaker does not play any sound, only through headphones.

---

### Post by pt-pepe78 on 2024-03-19
This seems to be resolved with kernel 6.8.0-11. Tested with Ubuntu daily build: [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)

---

### Post by MAFoElffen on 2024-03-19
So this works for DEV Noble 24.04?

---

### Post by pt-pepe78 on 2024-03-20
correct. just tested yesterday with their latest daily build and it was working as that is on kernel 6.8.0-11.

this also mentions that fix was already working with kernel 6.7.8-060708-generic
[https://askubuntu.com/a/1506684](https://askubuntu.com/a/1506684)
[https://askubuntu.com/questions/1486935/sound-not-working-after-update-lenovo-legion-7](https://askubuntu.com/questions/1486935/sound-not-working-after-update-lenovo-legion-7)

---

### Post by pt-pepe78 on 2024-03-20
The weird part is that with latest CachyOS ([https://cachyos.org/download/](https://cachyos.org/download/)) with linux kernel 6.8.1, this is not working. That would point the problem is not in the kernel, but somewhere in some settings file, which is fixed on Ubuntu?

---

### Post by jeremy-spagnet on 2024-07-17
> **pt-pepe78 said:**
> correct. just tested yesterday with their latest daily build and it was working as that is on kernel 6.8.0-11.

this also mentions that fix was already working with kernel 6.7.8-060708-generic
[https://askubuntu.com/a/1506684](https://askubuntu.com/a/1506684)
[https://askubuntu.com/questions/1486935/sound-not-working-after-update-lenovo-legion-7](https://askubuntu.com/questions/1486935/sound-not-working-after-update-lenovo-legion-7)


Those kernels all have the same audio issue (builtin speakers not working) for me - Ubuntu 24.04 LTS x86_64 on Legion 7 16IAX7

---

