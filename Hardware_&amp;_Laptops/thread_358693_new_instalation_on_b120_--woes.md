---
title: "new instalation on b120 --woes"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by valke on 2007-02-11
first off, i am very new to ubuntu, and to linux for that matter. i had ubuntu running fine in december, and attempted a swich to kde and blew everything up. i got frustrated and did a complete reinstall of edgy. now i cannot change my resolution to the standard 1280x800 for my laptop monitor. dell b120, 14.1, running i915. i have changed the conf file, and ran xserver-xorg but to no avail.

if at all possible, please walk me through step by step, or if someone has the same laptop with working resolution, would it work if i just copied and pasted your conf file? please and thank you.

---

### Post by valke on 2007-02-11
i really need help on this. please do help.

---

### Post by JesseLaw on 2007-10-18
This is an old thread, but for anyone else that has this problem:

just run from the terminal:

sudo aptitude install 915resolution

then enter your password. When it finishes installing just press CTRL-ALT-BACKSPACE to reboot X, and your resolution is correct.

---

