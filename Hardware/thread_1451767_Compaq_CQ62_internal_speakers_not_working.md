---
title: "Compaq CQ62 internal speakers not working"
date: 2010-04-11
forum: Hardware
---

### Post by chandru.in on 2010-04-11
I recently got a Compaq CQ62 laptop.  I'm unable to get any sound output from the laptop's internal altec lansing speakers.  While I get perfectly fine sound output if I connect a headphone.  It uses an intel sound card.

I'm using Ubuntu Lucid Beta 2 with all the latest updates installed.  Is there anyway I can get the internal speaker to work?

---

### Post by lidex on 2010-04-11
Enable your backports repo and install this:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```
Reboot. Check alsa-mixer settings.

---

### Post by chandru.in on 2010-04-11
That worked perfectly well.  I didn't even have to change settings in alsamixer.  Just installing that package did the trick.

---

### Post by lidex on 2010-04-11
Awesome. Wish they were all that easy!

---

### Post by chandru.in on 2010-04-12
I just found that while this made the laptop speakers work the headphones have stopped working.  Unmuting and setting the highest volume to everything on alsamixer didn't help either.

---

### Post by lidex on 2010-04-12
Can you post the output of these commands please:
```
aplay -l
head -n 1 /proc/asound/card*/codec#*
```
In a terminal="Applications>Accessories>Terminal"

---

### Post by chandru.in on 2010-04-13
**aplay -l**

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**head -n 1 /proc/asound/card*/codec#***

```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 270

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

```

**Note:** This is the output without installing *linux-backports-modules-alsa-lucid-generic*.  I had removed it as having the headphones working is more important to me than the laptop speakers.

---

### Post by lidex on 2010-04-13
The fact that the backports gave you sound through speakers shows updating the drivers does work, it's simply a matter of entering the the correct widget options into alsa-base.conf to get the headphones working.

In alsamixer did you scroll all the way over to the right for hidden options? Also try gnome-alsamixer. Select soundcard properties from the edit menu and make sure everything is enabled.

---

### Post by chandru.in on 2010-04-28
I've tried enabling all the options available in alsa mixer and it didn't help either.

---

### Post by lidex on 2010-04-28
OK. Try this. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel enable_msi=1  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by Machwe on 2010-07-05
> **lidex said:**
> Enable your backports repo and install this:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```Reboot. Check alsa-mixer settings.

Just thought I'd report that this worked for me on my HP G62. So thank you very much Lidex.

---

### Post by blairm on 2010-07-22
Just want to add my thanks to lidex - was going mad trying to get the sound going on this model!

Blair

---

### Post by sushilksk on 2010-07-25
> **lidex said:**
> Enable your backports repo and install this:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```
Reboot. Check alsa-mixer settings.
thanks, it works. both internal speakers and headphone jack. 
PS: mic worked after changing hardware profile.

thanks to lidex once again.

---

