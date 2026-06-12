---
title: "[SOLVED] Problems with sound since Ubuntu upgrade"
date: 2008-05-21
forum: Hardware
---

### Post by AlexPozz26 on 2008-05-21
Hi,

I recently updated to Ubuntu version 8.04 2.6.24-16, and since having done that, there will be times when the sound on my Dell Inspiron E1505 laptop stops working for no apparent reason. When this happens, some windows start to freeze, and I can't restart the proper way, and have to use the power button. Upon restarting, everything is back to normal. This happens about once a day, but sometimes more. This usually happens when I have firefox opened, and when it does happen, if I close firefox, I am unable to bring it back up again.

Please help,

Alex Poznanski

---

### Post by manualfaderen on 2008-06-05
Bump, I have the exact same problem, except I'm running a Lenovo T61. It's weird and awful!

---

### Post by kanishi on 2008-06-19
The problem also occurs with my laptop. It's a Toshiba M45.

---

### Post by phaedral on 2008-06-23
sudo /etc/init.d/alsa-utils reset

That's what worked for me.  Found it in the comments section at [http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

I'm running a newly upgraded U8 on a Compaq Presario V6000

---

### Post by Xi0N on 2008-06-23
Same happens here.-... specially if i try to open any youtube video while i listen to some music in amarok... besides not being able to heard the audio from youtube, after closig firefox, everything starts to hung up....
It comes happening since 8.04... and never happened before...... and also, i am using a normal desktop pc, so its nothing to do only with laptops

---

### Post by Stackmouse on 2008-06-26
Check out [http://ubuntuforums.org/showthread.php?t=828741]("http://ubuntuforums.org/showthread.php?t=828741") for a possible solution. Worked for my desktop.

---

### Post by Xi0N on 2008-06-26
Thanks for the help, i will try it when back at home and report my results ;)

---

### Post by Xi0N on 2008-07-01
> **Stackmouse said:**
> Check out [http://ubuntuforums.org/showthread.php?t=828741]("http://ubuntuforums.org/showthread.php?t=828741") for a possible solution. Worked for my desktop.

This solution worked perfectly, 

thanks!

---

### Post by Srikanth.Vittal on 2008-07-10
Hi

After I upgraded to Ubuntu 8.04, the sound was working, but distorted! The sound was not clear! The following fixed the issue:

sudo /etc/init.d/alsa-utils reset

Cheers
Srikanth

---

### Post by AlexPozz26 on 2009-01-12
typing "sudo /etc/init.d/alsa-utils reset" into the terminal worked for me! Thanks!

---

