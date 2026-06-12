---
title: "No System Sound on HP Pavillllllion dv9000 (Ubuntu 8.10)"
date: 2008-10-31
forum: Hardware
---

### Post by rugbeeprop on 2008-10-31
It seems that I am having System Sound problem in every *.10 release. When I installed 7.10, I didn't have any system sound. 8.04, the system sound came back, and now 8.10, it is gone again. Other sounds are fine (the boot up and login, music and video).

I started yesterday by upgrading straight from 8.04 to 8.10 using "Upgrade Manager". And decided to fresh install 8.10 this morning. Neither works.

Any suggestion?

P.S. this was my original 7.10 post: [http://ubuntuforums.org/showthread.php?t=583452](http://ubuntuforums.org/showthread.php?t=583452)

---

### Post by mempman on 2008-10-31
Are you sure you still have your codecs installed?  If you can play longin sounds, and other *.wav files, then you should be able to play mp3s - as long as you got proper codecs.

---

### Post by rugbeeprop on 2008-10-31
I have just downloaded the restricted drivers, so I can now hear MP3 by hovering the mouse cursor on MP3 file.

When I go to System --> Preferences --> Sounds, I am able to hear the system sounds (e.g. Alert Sounds, Button Clicked, Error, etc). It is when I actually click on a button or start a program or an error/warning message comes up, I hear nothing.

---

### Post by AmbiguousOutlier on 2008-10-31
I have a hp pavilion dv8000 and I cannot play system sounds either, only the logged on sound works, the rest including the login window sounds do not work. 

Do you think this is a hp thing?

---

### Post by AmbiguousOutlier on 2008-10-31
I have a hp pavilion dv8000 and I cannot play system sounds either, only the logged on sound works, the rest including the login window sounds do not work. 

Do you think this is a hp thing?

---

### Post by rugbeeprop on 2008-10-31
I am not fully sure. If you see my previous thread for 7.10 I did not received any final solution for it.

---

### Post by adammark on 2008-11-01
I am having the same problem with 8.10, its fully updated.

Laptop is HP dv9417ca

I am getting the logon sound, but no sounds after that.

---

### Post by rugbeeprop on 2008-11-03
I reinstalled 8.04 now. I do like the new features from 8.10, but I can wait until 9.04 to try again.

---

### Post by AmbiguousOutlier on 2008-11-03
Before I created a folder in my /Home directory which contained all the sounds I was trying to play. Once I copied them into /usr/share/sounds they worked. Although one of them is cut short, still trying to fix that.

---

### Post by rugbeeprop on 2008-11-03
The sounds that I used were the standard Ubuntu default system sounds.

---

### Post by rugbeeprop on 2009-03-10
Finally found the solution: [http://www.ubuntugeek.com/howto-enable-system-sound-in-ubuntu-intrepid.html](http://www.ubuntugeek.com/howto-enable-system-sound-in-ubuntu-intrepid.html)

---

### Post by rugbeeprop on 2009-03-18
Another thing that I noticed is that if I create a new profile with Ubuntu default setup, everything works perfectly (i.e. YouTube sound and Event sounds will appear on Logitech USB headset - when connected).

At this time, on my original account, Youtube and Event Sounds appears only on the laptop speakers, instead of the USB headset.

So I have a feeling that this has something to do with user's config file.

Does anyone know which file that I can go to edit, so that YouTube and Event Sounds will appear on the USB headset?

---

