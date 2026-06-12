---
title: "No sound in Ubuntu platform"
date: 2009-07-29
forum: Hardware
---

### Post by ashokshandilya on 2009-07-29
**I have installed Ubuntu on a vaio notebook VGN-T27GP/S running windowsXP. I have installed it on a new partition of 10GB.The installation is fine & every program is running except sound. There is no sound at all. **
[B]
When I work in Windows platform there i[/B]s **sound but in Ubuntu platform there is'nt. All configurations checked. Can anybody help? The driver in window's platform is _soundmax integrated digital audio_**. 
ashok shandilya

---

### Post by mikewhatever on 2009-07-29
Can you post the output of the following command from Applications->Accessories->Terminal:

**aplay -l**

---

### Post by rannable on 2009-07-29
Try 64bit ubuntu I had this on my Dell e5500, 64bit is way better...

---

### Post by Schjiskywuzz on 2009-07-29
I don't know if this will help you, but this is what I have to do, when I reinstall Ubuntu at my HP dv7 1070eo:

1) Open the Terminal.
2) In the terminal: type sudo gedit /etc/modprobe.d/alsa-base.conf
3) This will open that file In gedit: 
Scroll to the bottom of the file and add the new line:
*options snd-hda-intel enable_msi=1*
4) Save the file and close gedit (you can now also stop the terminal).
5) Reboot the computer 

Good luck

---

