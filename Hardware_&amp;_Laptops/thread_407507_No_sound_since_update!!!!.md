---
title: "No sound since update!!!!"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by BVBBQ on 2007-04-12
ok, edgy + my computer = hate.

when i first installed edgy on this comp the sound didnt work. i have an Intel Corporation 82801G (ICH7 Family) sound card. and i had to initially mess with it in order to get it to work, but that was a while ago and i dont remember what exactly i had to do. 

now. i have no sound again. since the last update. 

**double clicking on the sound control icon gives me this message:**

"No volume control GStreamer pluggins and/or devices  found"

**when i try to do an audio test i get:**

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
[B]
when i ls /dev/dsp i get:[/B]

ls: /dev/dsp: No such file or directory

any and all help would be greatly appreciated.

---

### Post by Rospo Zoppo on 2007-04-12
Please can you post the output of ```
cat /proc/asound/card0/codec#0 | grep -i codec 
``` ?

---

### Post by BVBBQ on 2007-04-12
cat: /proc/asound/card0/codec#0: No such file or directory

the only cause for all this malfunction i can think of is my girlfriend sticking princess stickers all over my tower.

---

### Post by Rospo Zoppo on 2007-04-12
Try following this [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by BVBBQ on 2007-04-12
ill try that, thanks.

---

### Post by treesurf on 2007-04-13
Reinstalling ALSA fixed it  for me.  I followed the directions in this thread:

[http://ubuntuforums.org/showthread.php?t=406676&highlight=sound+update](http://ubuntuforums.org/showthread.php?t=406676&highlight=sound+update)

---

### Post by Shinoda on 2007-04-14
If you don't want to compile ALSA yourself, try reinstalling it:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.

If you do or have to, follow e.g. [these]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") instructions or the ones at either the thread treesurf mentioned or the link Rospo Zoppo gave you.

---

### Post by apparatus on 2008-03-01
> **Shinoda said:**
> If you don't want to compile ALSA yourself, try reinstalling it:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.

If you do or have to, follow e.g. [these]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") instructions or the ones at either the thread treesurf mentioned or the link Rospo Zoppo gave you.

Thanks a lot, this solved it for me. Why did this problem even occur in the first place?

---

### Post by jjordan on 2008-03-01
just reinstall Alsa each time you change the kernal.  I am used to it!  Don't forget to copy or symlink like the link above advises.  

 -j

---

### Post by Yellow Pasque on 2008-03-02
This is kind of dangerous with all the dependencies. It would be much better to build ALSA yourself, which is really easy with these scripts:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

