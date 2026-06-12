---
title: "Replacing motherboard"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Bluecube on 2007-05-20
I'm going to be replacing my motherboard at sometime in the very near future and I'm wondering what affect this will have on my Feisty install. Is it like Windows where you need to reinstall to avoid any problems or will everything work just fine?

TIA

---

### Post by Kobalt on 2007-05-20
There is a chance it will work but it could also leed to some hardware not being activated/usable. If I were you I would do a clean install, just to make sure...

---

### Post by lw5 on 2007-05-20
Although it is advisable to re-install, I recently replaced my motherboard and processor (Gigabyte socket A mobo with an AMD sempron 2600+) with a dual Xeon (2x 2,4Ghz) setup. It worked immediately. I was forced to re-install because Windows wouldn't play nice (and I probably still could have prevented to re-install Ubuntu but I didn't).

---

### Post by Bluecube on 2007-05-20
By "worked immediately" do you mean that the new mobos features and the dual CPU setup was detected and useable or simply that Ubuntu worked with a few odds and ends broken?

If a reinstall is necessary is there any quick way to restore progrma settings and email?

---

### Post by lw5 on 2007-05-21
No, if I would have kept my old installation, I would have needed to replace my kernel with an SMP (multi proc/core) kernel. So initially I could only use one processor, the rest just worked. But I'm not saying this will be true for you as well! I just tried it to find out if it would and it did :)

If you do a re-install, back up your /home/$user folder (your home folder) as it contains all you preferences (the .file files) and your /etc (all configuration files). Just copy them over after the installation as needed.

I'm not sure where your mail is stored, but it should be easy to find out.

---

