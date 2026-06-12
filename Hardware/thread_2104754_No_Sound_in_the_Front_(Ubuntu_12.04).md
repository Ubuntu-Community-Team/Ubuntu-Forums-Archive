---
title: "No Sound in the Front (Ubuntu 12.04)"
date: 2013-01-14
forum: Hardware
---

### Post by gsrafael on 2013-01-14
I'm a newbie on Linux, and I'm using Ubuntu 12.04. The problem is: I have a VIA VT1705 audio card and the back ports are working well, but there's no sound in the Panel USB Audio Mic (for the headphone). I already read some other posts here, but none of them helped me fix this.

---

### Post by gsrafael on 2013-01-14
> **gsrafael said:**
> I'm a newbie on Linux, and I'm using Ubuntu 12.04. The problem is: I have a VIA VT1705 audio card and the back ports are working well, but there's no sound in the Panel USB Audio Mic (for the headphone). I already read some other posts here, but none of them helped me fix this.

I'm almost giving up on this and going back to Windows... Anyone?

---

### Post by ssrublev on 2013-02-25
Try to execute alsamixer in terminal. Do you see green ">" symbols on the right side of the frame? Move cursor to the rightmost field AND THEN FURTHER &#8212; THERE ARE MORE OPTIONS. Or you can STRETCH terminal window wider until you see all of the controls. See the screenshot here: [http://www-developer.blogspot.ru/2012/12/hda-intel-via-vt1705-ubuntu-12041210.html](http://www-developer.blogspot.ru/2012/12/hda-intel-via-vt1705-ubuntu-12041210.html)

You probably need to turn on "Smart 5.1" (by pressing M key!) and then switch "Independent" on or off.

If this doesn't work, then you probably also have to add "options snd-hda-intel model=auto" string to "alsa-base.conf" file as described here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

(I first modified the file and when it didn't work found alsamixer solution, don't know if it's obligatory to have both options done)

---

