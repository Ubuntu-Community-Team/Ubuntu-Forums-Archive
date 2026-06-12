---
title: "Audio Hardware Disappeared After 9.10 Upgrade"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by drhiii on 2009-11-12
I have searched the forums and am not finding the answer.

Upgraded from 9.04 (working perfectly) to 9.10.  A few things broke, all fixed.  Except...

There are no audio hardware devices available in the Sound Preferences/Hardware.  Consequently, no sound.

Anyone point to a thread or idea on where to find solutions?  I don't want to reinstall, or go back to 9.04, but am on the cusp of that.  

tx


PS, I was able to boot into 9.10 Test CD and audio worked fine.  It found the hardware device.  Hardware device in the upgraded 9.10 from 9.04 disappeared as stated above.  Help?

---

### Post by //yardo on 2009-11-12
I'm having similar problems. Same thing. 9.04 worked just great with no problems... now my audio device is visible but no sound at all. I've played with different settings and can't get any audio.

---

### Post by Judders on 2009-11-13
I have the same problem. Sound was working fine until upgrade.
No Hardware detected

---

### Post by thehud on 2009-11-20
I have similar symptoms, but after a fresh install - Yardo - You say you managed to get your hardware recognised - How did you do that exactly? If you can remember that is.

My hardware is (lspci):
```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```On board audio, 7.1 surround.

There seems to be plenty of threads about distorted sound - but not about no hardware in the sound preferences dialogue.

James.

... I say it was a clean install, I'm still using my old /home dir from Jaunty... let me get rid of the old pulse and alsa config before I reboot. Maybe it'll help...

[EDIT]

Yes, that helped. Now I have the hardware listed in the Sound Preferences. I deleted my ~/.pulse/ dir and ~/.pulse-cookie file. Now to see what comes next.

Seems that I was able to select one of the unknown Pulse devices in the multimedia selection window... But now I have the popping problem (which is improved but not alleviated by setting the hardware profile to analogue surround 4.1, rather than 5.1, in the sound preferences.

Gah. Anyone else found anything?

---

### Post by timb_nz on 2009-12-09
> **drhiii said:**
> I have searched the forums and am not finding the answer.

Upgraded from 9.04 (working perfectly) to 9.10.  A few things broke, all fixed.  Except...

There are no audio hardware devices available in the Sound Preferences/Hardware.  Consequently, no sound.

Anyone point to a thread or idea on where to find solutions?  I don't want to reinstall, or go back to 9.04, but am on the cusp of that.  

tx


PS, I was able to boot into 9.10 Test CD and audio worked fine.  It found the hardware device.  Hardware device in the upgraded 9.10 from 9.04 disappeared as stated above.  Help?

Similar situation here, but I was using Kubuntu 9.04 working nearly perfectly (sound was working).

I did a clean install of Ubuntu 9.10, but sound is not working, and the hardware list is blank (when I open Sound Preferences)
Alsamixer shows HDA Intel, Realtek ALC660-VD
I am using a laptop...

Any suggestions?

Thanks,
Tim

---

### Post by drhiii on 2009-12-12
So the solution is a fresh install?

Lots of things broke in 9.10 upgrade it appears...

---

### Post by winstonkirk on 2009-12-13
Same problem, upgraded to 9.10 and there is no audio device listed.

---

### Post by timb_nz on 2009-12-17
Clean install did not fix it.
I uninstalled and reinstalled the sound following the instructions for sound problems, but that only fixed it for one boot.

---

### Post by timb_nz on 2009-12-18
I uninstalled the PulseAudio Drivers and this seems to have fixed the problem

---

### Post by Djovik on 2011-01-20
> **winstonkirk said:**
> Same problem, upgraded to 9.10 and there is no audio device listed.
I have also the same problem. In ubuntu 9.10 , no hardware listed.

---

