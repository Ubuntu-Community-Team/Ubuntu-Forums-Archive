---
title: "Login sound lags"
date: 2008-11-24
forum: General Help
---

### Post by Shachiel on 2008-11-24
Hello,

When I start my computer and get to the login window the drums (question.wav) take around 20 seconds to play, this has only happened since I made a fresh installation of Intrepid, had Hardy before and Gutsy earlier and none of them showed this error. Can anyone please tell me if this is a common bug or how could I fix it?

Thanks in advance,

---

### Post by swoody on 2008-11-24
Sounds kind of simple, but have you tried disabling the startup sound in System>Administration>Login Window and then rebooted? Then re-enable the sound and reboot again?

---

### Post by blazemore on 2008-11-24
I had this problem.
What solved it was boot profiling.
On GRUB, hit e to edit the commands before booting, then add the word profile to the end of the boot options. Hit escape and then b to boot. It will take longer, but then when it's booted up, reboot and a) your sound should be fixed, and b) your system could boot up to 10 seconds faster!

---

### Post by Shachiel on 2008-11-27
I tried both suggestions and none of them worked really... However thanks blazemore, even though the sound wasn't fixed my boot time did speed up.

---

