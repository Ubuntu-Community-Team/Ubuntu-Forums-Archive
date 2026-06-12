---
title: "HDA Intel&amp; Asus M51Va - no sound."
date: 2008-12-28
forum: Hardware
---

### Post by sparrow88 on 2008-12-28
Only sound I can hear is a test sound in System->Preferences->Sound. No system sounds, no Mp3 etc. I have upgraded ALSA to newest version, but it didnt work. 
Thanks in advance for replies.

EDIT.
I have been typing many things in 
```
/etc/modprobe.d/alsa-base
```
like 
```
options snd-hda-intel model=3stack-dig
```
I ve also typed: "lenovo", "m51va". 
It didnt help.

---

### Post by hotweiss on 2008-12-28
> **sparrow88 said:**
> Only sound I can hear is a test sound in System->Preferences->Sound. No system sounds, no Mp3 etc. I have upgraded ALSA to newest version, but it didnt work. 
Thanks in advance for replies.

Try this:

A) First we&#8217;ll have to edit the ALSA configuration file via terminal:
sudo nano /etc/modprobe.d/alsa-base

B) Scroll down to the bottom and add this line:
options snd-hda-intel model=haier-w66

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Reboot

If it doesn't work, just undo what you just did.

This solution worked for my Asus M50Sv-A1.

---

### Post by sparrow88 on 2008-12-28
There is no any change. Anyway I am glad you replied so fast :>

---

### Post by JeanJean on 2008-12-28
Can you post output of:

```
lspci | grep Audio
```

Are you sure all channels are unmuted in alsa-mixer ?

---

### Post by hotweiss on 2008-12-28
This might actually work:

A) First we’ll have to edit the ALSA configuration file via terminal:
sudo nano /etc/modprobe.d/alsa-base

B) Scroll down to the bottom and add this line:
options snd-hda-intel model=m51va

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Reboot

---

### Post by sparrow88 on 2008-12-28
```
sparrow@sparrow-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

```


> This might actually work:

A) First we&#8217;ll have to edit the ALSA configuration file via terminal:
sudo nano /etc/modprobe.d/alsa-base

B) Scroll down to the bottom and add this line:
options snd-hda-intel model=m51va

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Reboot
[quote="sparrow88"]I ve also typed: "lenovo", "m51va".
It didnt help.[/quote]

> 
Are you sure all channels are unmuted in alsa-mixer ?
Well... In fact I am not sure. My master volume is 100%, and all things in sound preferences are set to ALSA. Dunno what do you mean by saying "all channels". CAn you give me any hints where to check this? I would not say I am an expert when it comes to deal with Linux.

---

### Post by AopicieR on 2008-12-28
I also have an HDA Intel Chip and I have to install the linux-backports-modules to get it working.
In order to do this, you have to open your /etc/apt/sources.list and comment in the backports repository.
In my version this is done by removing the # at the beginning of the lines
```
#deb http://de.archive.ubuntu.com/ubuntu intreprid-backports main restricted universe multiverse
#deb-src http://de.archive.ubuntu.com/ubuntu intreprid-backports main restricted universe multiverse
```
Then you can use Synaptic to install the modules. Search for linux-backports-modules and install the version matching your kernel. For me, this is
```
linux-backports-modules-2.6.27-9-generic
``` 
Hopefully sound will work after rebooting.

---

### Post by hotweiss on 2008-12-28
Yes, getting the sound working properly is sometimes very frustrating. I couldn't get it working properly for weeks, and then someone game me the haier extension which surprisingly worked with my Asus notebook.

---

### Post by JeanJean on 2008-12-29
> Well... In fact I am not sure. My master volume is 100%, and all things in sound preferences are set to ALSA. Dunno what do you mean by saying "all channels". CAn you give me any hints where to check this? I would not say I am an expert when it comes to deal with Linux.

Double click on alsa mixer, than check of this sliders are pushed up: Master, PCM, Front, CD.

---

### Post by batteryfast on 2008-12-29
I purchase a new laptop recently. However, my litter baby damage the [asus battery](http://www.batterygoshop.co.uk/asus/), So we have to puchase new one.

---

