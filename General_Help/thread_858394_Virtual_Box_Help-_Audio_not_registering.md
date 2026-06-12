---
title: "Virtual Box Help- Audio not registering"
date: 2008-07-13
forum: General Help
---

### Post by Edigido on 2008-07-13
Okay, so I installed XP onto the virtual box, and everything seems to work great.  However, the audio isn't working for anything.  I looked at the audio settings, and no audio device was appearing to be installed.  I'm pretty sure I mounted the audio device in the setting area, and used the Pulse Audio and the Soundblaster.  I'm on a Lenovo laptop (T61 if that helps anyone), so the speakers are built in.  

Anyone have any ideas for my predicament?

---

### Post by Dicinox on 2008-07-13
See in the configuration of the virtual machine, look for the sounds settingns and see that it's not in audio null

---

### Post by Edigido on 2008-07-13
It's not.  The Host audio driver is OSS, and the Audio Controller is ICH AC97

---

### Post by tech0007 on 2008-07-13
Check the device manager in XP guest. If there's an (!) or (?) on multimedia audio controller, right click update driver.

---

### Post by Edigido on 2008-07-13
I can't seem to find the Device Manager in XP.

---

### Post by tech0007 on 2008-07-13
Start-> rightclick My Computer -> click Properties. Click Hardware tab, then device manager button.

---

### Post by Edigido on 2008-07-13
There weren't any Question marks, nor exclamations.

---

### Post by tech0007 on 2008-07-13
Turn off the guest OS, then try each sound server in Virtualbox (ALSA, Pulse and OSS). If you Ubuntu machines' sound is ok, it should also work w/ the gues VMs.

---

### Post by Edigido on 2008-07-13
YES!!! It works!  Thanks everyone ^_^

---

### Post by tech0007 on 2008-07-13
NP. Dont forget to mark this thread as resolved.

---

### Post by br3athe on 2008-11-23
hi 
ive got the same problem , I have oss , alsa and pulse as the host audio driver 
and ac97 or soundblaster as the audio controller , I have turned off the virtual machine , and cannot seem to test any of these combinations , I have tried them all and gone through the above thread when xp is up 
i am using ubuntu 8.10 and vb 2.04 
any ideas how I can continue 
thanks

---

### Post by Antman on 2008-11-27
> **br3athe said:**
> hi 
ive got the same problem , I have oss , alsa and pulse as the host audio driver 
and ac97 or soundblaster as the audio controller , I have turned off the virtual machine , and cannot seem to test any of these combinations , I have tried them all and gone through the above thread when xp is up 
i am using ubuntu 8.10 and vb 2.04 
any ideas how I can continue 
thanks
You should start a new thread so people will see it.

---

