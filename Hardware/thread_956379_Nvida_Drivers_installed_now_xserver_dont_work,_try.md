---
title: "Nvida Drivers installed now xserver dont work, tryed it all"
date: 2008-10-23
forum: Hardware
---

### Post by Phattypab on 2008-10-23
hey im new to linux and iv been trying to install the nvidia drivers, i think i managed to install them but now xserver wont show up, i type "sudo /ect/init.d/gdm start" but it wont work it comes back with
"file not found" or something similar

i think the nvidia drivers have screwed up my xorg.conf

i try recovery mode and tried fixing everything and i tried ctrl alt f1 and f2 est...

but nothing works i also tried envy and it didnt uninstall or install. it come back with "you have no desktop installed"

what shall i do? i dont mind formatting but i dono if i can install the drivers again.

i have a gtx 280 BFG if that helps at all

thanks lots :D

---

### Post by Phattypab on 2008-10-24
Bump...

---

### Post by cicatrix1 on 2008-10-24
Please post:

egrep 'EE|WW' /var/log/Xorg.0.log

along with your xorg.conf

---

### Post by Phattypab on 2008-10-24
im really but im a noob, how do i do that?
keeping in mind that i only have the commandline avalable.

thanks!

---

### Post by Phattypab on 2008-10-24
hey i figured out where the files are coz i can see them in winodws but i cant open the files to view the logs and i cant attach the files.

sorry :( i am a total n00b....

---

### Post by cicatrix1 on 2008-10-24
Hm.  From the command line, do:

egrep 'EE' /var/log/Xorg.0.log

there shouldn't be too many entries, I'd suggest writing them down.  Maybe try googling any errors you see there.  Basically what that does is check Xorg (the "graphical" part of linux) logs and show you what it considers to be an error.

---

### Post by Phattypab on 2008-10-24
absolutly nothing shows up, it just make a new line that is TOTALY blank

---

