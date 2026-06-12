---
title: "Soundcard"
date: 2010-09-14
forum: Hardware
---

### Post by biokahuna on 2010-09-14
I am an absolute neophyte and greatly technically challenged. Any and all help would be hugely appreciated ASAP. I have a Gateway NV79 laptop and ordered it with Windows 7, woe is me. A friend did install of Ubuntu and my sound card shows as recognized but does not work. I assume that this is a driver issue. Can someone please help.

---

### Post by solar george on 2010-09-15
Enable "Unsupported Updates (backports)" in software sources (see the software management section of [http://ubuntu-manual.org/](http://ubuntu-manual.org/) for more details) and then install [linux-backports-modules-alsa-lucid-generic]("apt://linux-backports-modules-alsa-lucid-generic") to make sure you have the latest sound drivers available.

---

### Post by cascade9 on 2010-09-16
Check the mixer to make sure that its not muted (been caught by that a few times myself)

---

### Post by lidex on 2010-09-17
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-dig 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by lkjoel on 2010-09-25
> **biokahuna said:**
> I am an absolute neophyte and greatly technically challenged. Any and all help would be hugely appreciated ASAP. I have a Gateway NV79 laptop and ordered it with Windows 7, woe is me. A friend did install of Ubuntu and my sound card shows as recognized but does not work. I assume that this is a driver issue. Can someone please help.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

