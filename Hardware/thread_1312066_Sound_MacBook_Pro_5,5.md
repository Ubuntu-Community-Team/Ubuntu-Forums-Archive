---
title: "Sound MacBook Pro 5,5"
date: 2009-11-02
forum: Hardware
---

### Post by needTOS on 2009-11-02
Hello everyone, was having trouble with installing the sound driver on a MacBook Pro 5,5 (13inch). I am running Ubuntu 9.10 32-bit (was running 64-bit but had the same trouble). I followed the instructs here [https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic)
and no matter how many times I try it on 32-bit or 64-bit I can not get the sound to work. Is anyone else having the same problem? Or are there others that can't get them to work according to the instructions. A little help would be nice guys, I am not new to Ubuntu been using it since it's original release (Warty 4.10). 

Thanks for the help guys,
Steve

---

### Post by kettle on 2009-11-04
I had the same issue with the 5,5 15inch.  

I had to restart the machine for the changes to take effect.  After that I ran,

$ gnome-alsamixer 

and set the surround sound to 'on' and cranked up the volume.  After that everything worked.

---

### Post by needTOS on 2009-11-04
Yea mate the thing is I've done it. I've reinstalled several times. And followed the instructions word for word. And I unmute it all, crank the volume up and still nothing.

-Steve

---

### Post by Cerin on 2009-11-06
I have the same problem. I installed 64-bit 9.10 on a MacbookPro5.5, and followed the sound setup instructions at [https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Sound) but it doesn't work.

Although the author's instructions seemed out-of-sync with the actual software. He says to switch the driver to ALSA in the Sound Preferences dialog, but there's no such option.

---

