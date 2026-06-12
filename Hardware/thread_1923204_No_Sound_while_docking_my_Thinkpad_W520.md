---
title: "No Sound while docking my Thinkpad W520"
date: 2012-02-10
forum: Hardware
---

### Post by produnis on 2012-02-10
Hi folks,
I finally managed to connect my ThinkPad W520 to the Lenovo Docking Station 3.
It was quit hard job to enable my two external monitors, which are connected to the dock . 

anyhow,
what I cannot set up is the sound jack.
If connected to the dock, I have no sound.
If I un-plugg the speakers from the dock's jack, then sound is played through my ThinkPads own speakers.
If I connect the speakers to the ThinkPad's audio-jack, then sound is played
But: If I connect the speakers to the dock's audio-jack, then nothing is played.

This is funny, because yesterday it finally worked (at the end of the day), and since today sound is dead again.

I have no idea why it finally worked yesterday, and why I does not work anymore today...


Does anyone made the Dock's audio jack work?

---

### Post by produnis on 2012-02-10
I just solved my problem by adding the following to 

/etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=thinkpad
```


After rebooting, sound comes through the docking station...

---

### Post by diffuser78 on 2012-05-11
> **produnis said:**
> Hi folks,
I finally managed to connect my ThinkPad W520 to the Lenovo Docking Station 3.
It was quit hard job to enable my two external monitors, which are connected to the dock . 

anyhow,
what I cannot set up is the sound jack.
If connected to the dock, I have no sound.
If I un-plugg the speakers from the dock's jack, then sound is played through my ThinkPads own speakers.
If I connect the speakers to the ThinkPad's audio-jack, then sound is played
But: If I connect the speakers to the dock's audio-jack, then nothing is played.

This is funny, because yesterday it finally worked (at the end of the day), and since today sound is dead again.

I have no idea why it finally worked yesterday, and why I does not work anymore today...


Does anyone made the Dock's audio jack work?


Can you please share how you worked the two monitors to work on the docking station for the thinkpad ?

---

### Post by lunatico on 2012-07-24
> **produnis said:**
> I just solved my problem by adding the following to 

/etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=thinkpad
```


After rebooting, sound comes through the docking station...

I can confirm this worked for me.
Running Linux Mint 13 Cinnamon 32-bit on a Thinkpad W520.

---

### Post by produnis on 2012-07-24
> **diffuser78 said:**
> Can you please share how you worked the two monitors to work on the docking station for the thinkpad ?

I used "disper" to do so.

check this page for more information
[http://www.produnis.de/blog/?p=1506](http://www.produnis.de/blog/?p=1506)

(yes, it is in german language, but the commands should give you the hints)

-------------
Edit:

Install disper:

> sudo add-apt-repository ppa:disper-dev/ppa
sudo apt-get update
sudo apt-get install disper

if the thinkpad is NOT connected to dock, type in:
disper -l # this will list all monitors

With my machine, it gives me this:
> display DFP-0: LEN
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 960x720, 1024x768, 1152x864, 1360x768, 1280x960, 1440x900, 1280x1024, 1400x1050, 1600x1024, 1680x1050, 1920x1080

This is my laptop-monitor, showing all possible display-resolutions

Now, connect your thinkpad to the docking station and type in:
disper -l

with my machine, it gives me:
> display DFP-0: LEN
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 960x720, 1024x768, 1152x864, 1360x768, 1280x960, 1440x900, 1280x1024, 1400x1050, 1600x1024, 1680x1050, 1920x1080

display CRT-0: FUS B19-3
 resolutions: 320x240, 400x300, 512x384, 680x384, 640x480, 720x450, 700x525, 840x525, 800x600, 960x540, 832x624, 960x600, 1024x768, 1152x864, 1360x768, 1280x960, 1440x900, 1400x1050, 1680x1050, 1920x1080, 1280x1024

display DFP-2: Samsung SyncMaster
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 960x720, 1024x768, 1152x864, 1280x960, 1280x1024

You can see the two monitors of the docking station, named "CRT-0" and "DFP-2" (might be different to your system)

Now, to switch off the laptops display, and to activate the two external displays, type in:
> disper -e -d CRT-0,DFP-2
-e is for "expand the display"
-d says wich displays to use (in this case "CRT-0" and "DFP-2")

Voila

To switch back to the laptops own display type in:
display -s # single display

thats all
;)

---

### Post by pgpayton on 2012-11-08
I encounter the same problem, this is really help, thank you!!!!

---

