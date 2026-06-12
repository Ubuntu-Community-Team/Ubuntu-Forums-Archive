---
title: "How do i install i .run file"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by vistadude on 2008-12-23
I downloaded the game Wolfenstein: Enemy Territory from file planet, and i downloaded the linux version, not windows. The file i downloaded was called et-linux-2.60.x86.run my question is, how do i install that?

---

### Post by SuperSonic4 on 2008-12-23
```
cd ~/Desktop
chmod +x et-linux-2.60.x86.run 
./et-linux-2.60.x86.run 
```

change the ~/Desktop to wherever the file is

cd is change directory
chmod +x is make executable
./et-linux-2.60.x86.run is run the file

---

### Post by inobe on 2008-12-23
**sudo nautilus** in terminal if the file is saved in nautilus.

after that' click the .run file' then select open with terminal, the installation will begin.


be careful, this will allow you super user privileges.

edit: try the first suggestion before this one, others may not agree to my suggestion due to security reasons.

---

### Post by oldos2er on 2008-12-23
"**sudo nautilus** in terminal if the file is saved in nautilus."

 Use "gksu nautilus" instead. Here's why: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by inobe on 2008-12-23
there you have it, i knew that was coming...

because it has security issues, it is meant as a last resort.

---

