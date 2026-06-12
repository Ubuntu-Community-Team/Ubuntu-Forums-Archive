---
title: "Webcam/Suspend Issue!"
date: 2010-04-16
forum: Hardware
---

### Post by tmx84 on 2010-04-16
Everytime i close the lid and reopen, or suspend the laptop, when i resume the Webcam turns on (the little green light next to the webcam is on is how i know it's on).  So i always have to open terminal run guvcview and then close it to turn the webcam off.  I'm running 64bit 10.04!  The laptop is a Asus K50I.

---

### Post by tmx84 on 2010-04-18
Help please! Is there any command line for UVC to turn off the webcam that i can just add to the resume script?!

---

### Post by Ni85 on 2010-05-09
has anyone found a solution for this?
i have always had this issue, but now with lucid i'm resolved to fix it.
running on an asus too...

---

### Post by tmx84 on 2010-05-09
What i ended up doing was going into /etc/pm/config.d made a file named webcam with SUSPEND_MODULES=uvcvideo in the file. And it's fixed the issue...

---

### Post by Ni85 on 2010-05-10
fixed it for me too :)
thanks a lot

---

