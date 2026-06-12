---
title: "Problems with garmin etrex vista in Ubuntu"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by alhanduin on 2007-11-12
Please i need help! 

I'm a spanish boy with problems in ubuntu to run a gps garmin etrex vista. 

I'll explain my problem: I bought a garmin etrex vista gps with serial232 conector, but i have ubuntu gutsy in a portatil pc so i can't use serial port. Then i bought a serial-usb adapter and i was so happy cause i think that i colud run my gps!!! But when i conected it into the USB port didn't run! Anything ubuntu didn't do anyting.... It didn't mount the usb device and i don't understand why cause i have listened that the gutsy version recognizes automatically the gps....

Please help me... Think that i'm so new in the ubuntu comunity so please explain me so slowly and easyly...

Aps and excuse me for my writting fails... 

Thanks!

---

### Post by kubunterix on 2007-11-14
Hi alhanduin,

i was fighting hard with a gps device (garmin geko) and ubuntu. Found some solutions.

A) Using gpsdrive, gpsbabel & co i had to remove the brltty package. (see: [https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/7438](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/7438))
But never got success with uploading tracks.

B) My one and only step "towards" Windows: Using Virtualbox 1.5 and emulating a Windows XP. It is possible to loop the usb port into the virtual system. Then using software for windows. hmm. hmmm.

Best regards,

Richard

---

### Post by gerkin on 2007-12-21
For Garmin eTrex yellow see my post here: [http://ubuntuforums.org/showthread.php?p=3994981#post3994981](http://ubuntuforums.org/showthread.php?p=3994981#post3994981)

---

