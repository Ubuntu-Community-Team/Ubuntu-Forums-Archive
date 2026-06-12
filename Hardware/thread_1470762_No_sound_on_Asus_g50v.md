---
title: "No sound on Asus g50v"
date: 2010-05-03
forum: Hardware
---

### Post by blackfox on 2010-05-03
I recently updated from Ubuntu 9.10 to 10.04. Since then, sound isn't working. on Ubuntu 9.10 I added, "options snd-hda-intel model=g71v probe_mask=1" line on alsa-base.conf file and everything worked fine. But on Ubuntu 10.04 it doesn't seem to fix the problem. 

Anyone know a fix for this?

---

### Post by blackfox on 2010-05-03
okay, I've fixed this.

---

### Post by Silver Knight on 2010-07-20
> **blackfox said:**
> okay, I've fixed this.

Hi.  Happy you fixed it, but for the benefit of others with this same issue who may arrive at this post via Google as I did, I'd like to request further details on what exactly you did to fix this.  :)

---

### Post by lidex on 2010-07-20
You might try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=g50v 
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

### Post by omer.qadir on 2010-09-21
> **blackfox said:**
> I recently updated from Ubuntu 9.10 to 10.04. Since then, sound isn't working. on Ubuntu 9.10 I added, "options snd-hda-intel model=g71v probe_mask=1" line on alsa-base.conf file and everything worked fine. But on Ubuntu 10.04 it doesn't seem to fix the problem. 

Anyone know a fix for this?
actually, you don't need to change the g71v line to g50v. You probably used it (like i did) to get the headphone jack working. So if you keep that line in the alsa-base.conf file, but simply fix the alsamixer levels, it should be alright. At least for me, I found that I only had to turn up the speaker level in alsamixer.
good-luck!

---

### Post by lkjoel on 2010-09-24
> **blackfox said:**
> okay, I've fixed this.
Could you mark this as solved then?

---

