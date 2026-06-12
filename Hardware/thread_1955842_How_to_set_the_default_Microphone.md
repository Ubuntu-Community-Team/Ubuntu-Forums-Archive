---
title: "How to set the default Microphone"
date: 2012-04-10
forum: Hardware
---

### Post by kmh42 on 2012-04-10
My mother using an external Web-cam with a Microphone. The PC doesn’t recognise the  Microphone automatically. So I always have to activate it myself in the  Audio Settings as Audio Input device after a restart. How can I avoid this and set it as default Microphone.
  This PC doesn't have another Webcam or Mic. And the Web-cam is always pluged in.


  Ubuntu 12.04 beta with latest updates (I also had this problems with 10.04)
Logitech, Inc. Web-cam B500

---

### Post by kuvanito on 2012-12-02
i feel your pain
been having this problems for quite sometime
gave up and manually chose my webcam every boot :(

---

### Post by StephenG on 2012-12-26
Same pain here.  My audio settings list 3 or 4 other mic choices for mics that don't even exist on my system.  It'd be delightful to figure out how to choose the webcam mic as the only choice and delete all those other phantom choices - causing the system to default to it.  Anyone?  (I'm far too new at this OS, and have no programming experience, to navigate the mine fields.)

---

### Post by kuvanito on 2012-12-26
well,if you manage to manually select your mic and after a test you can open up the terminal Crtl+Alt+T and then enter this command:sudo alsactl store
this will help to hold your default mic until things change and once again when you managed to select it re-type the command in the terminal.Happy New Year. ):P

---

