---
title: "ubuntu not booting grldr"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by tomocar on 2009-04-13
i installed ubuntu, and when it said that i need to restart the computer i did that. Than i had the option to chose between ubuntu and XP, and i chose ubuntu... and than the screen came up saying booting GRLDR and nothing else happened afterwards... please help. 

thank you

---

### Post by Aubergines on 2009-04-13
As far as I can hunt around GRLDR is Grub4dos or wingrub and it's a patched version of regular Grub. Not sure what that's doing in Ubutnu, more likely it's a left over from Windows Vista since I hear there's some "dodgy" Vista distros often use GRLDR to avoid activation.

---

### Post by tomocar on 2009-04-13
i never installed vista on my computer...
i asked this same question on yahoo and got this answer:

grldr is used by windows to load grub. If grldr hangs then it can't find /boot/grub/menu.lst on your ubuntu partition.

i have the menu.lst file under D:/winboot/menu.lst

maybe this is the problem? if not... i have no idea o.0

---

### Post by Aubergines on 2009-04-13
Not sure, I'd say the easiest option would be to get Linux grub to boot windows rather than the other way around so menu.lst used is from linux. I don't know anything about GRLDR but I assume it's possible that the menu.lst in D:/winboot/menu.lst is the grub config used by GRLDR and not linux grub.

---

### Post by Aubergines on 2009-04-13
Hmm unless it's some weird [Wubi](http://wubi-installer.org/) thing.

---

### Post by tomocar on 2009-04-13
> **Aubergines said:**
> Not sure, I'd say the easiest option would be to get Linux grub to boot windows rather than the other way around so menu.lst used is from linux. I don't know anything about GRLDR but I assume it's possible that the menu.lst in D:/winboot/menu.lst is the grub config used by GRLDR and not linux grub.

ahh... the menu.lst is under D:/ubuntu/winboot/menu.lst

how can i get the linux grub to boot windows?

---

### Post by tomocar on 2009-04-13
i'll tell you exactly what i did... my father brought me linux cd and i tried to install... i installed normally, and when restarting computer got the booting grldr screen... i thought it was something wrong with the cd... than i downloaded ubuntu from linux webpage, installed it and got the same "error" i have no idea what to do now...

---

### Post by Aubergines on 2009-04-13
I'm not too sure, wubi is something I've never used before. Have you tried installing Ubuntu by booting off the cd directly rather than installing it via windows?

---

### Post by tomocar on 2009-04-13
yeah... it's the same... and when i try only the test linux without installing, an error pops up saying that it couldnt find the right CD or something like that... i guess its something wrong with hardware rather than with software...

---

### Post by tomocar on 2009-04-13
another thing happens now... when i start my computer and chose ubuntu and the ubuntu not booting grldr shows, right after that the computer reboots... and it keeps doing it...

---

### Post by randomnosity on 2009-04-19
i had the same problem discussed in this thread. i tried nearly everything here. I managed to change the bios to boot priority to boot from CD first rather than the hard drive.

hope this works

---

