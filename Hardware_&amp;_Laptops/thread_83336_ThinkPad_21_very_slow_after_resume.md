---
title: "ThinkPad 21 very slow after resume"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by tp21 on 2005-10-28
hi,
i am running Ubuntu 5.10 on IBM TP T21, everything works very well, except suspend, or accuratly resuming from suspense(apm -s). after resume the machine is very very slow. it takes minutes to open programmes like terminal or even just to logout. and only reboot helps.
i also noticed that programms like gimp or openoffice are relatively faster than the system programms after resume, but still slow compared to after boot.
after resume it is immpossible to save a document with gedit, but openoffice can do that!!
there is a bug concerning this behaviour in bugzila([http://bugzilla.ubuntu.com/show_bug.cgi?id=15121)](http://bugzilla.ubuntu.com/show_bug.cgi?id=15121)), but i would like to ask if you have any ideas? it is very tyring to reboot every time.
the machine has enough ram(384mb), and acpi=off.
thanks in advance

---

### Post by tp21 on 2005-10-31
hi,
just in case somebody faces the same problem, i found out that swithing off the event sound(from audio setting) makes the computer comes back to its normall speed. in other words thus bug is a sound bug, for some reasons after resume sound would hang.
i do not know how sound works under ubuntu, is there a sound server which i can reboot? or how can i make further debuging?
thanks and greetings.

---

