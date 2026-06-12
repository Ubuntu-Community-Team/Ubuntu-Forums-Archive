---
title: "Gpu information"
date: 2010-04-01
forum: Hardware
---

### Post by AlexRamallo on 2010-04-01
ok, this computer is a complete piece of crap. It doesn't even have 1GB of memory, and I'm not even sure what type of graphics card it has -.-

Is there a way to see my graphics card, and maybe other hardware info? I'd like to see if theres any hope for this computer before I throw it away :|

---

### Post by gordintoronto on 2010-04-01
Administration/sysinfo will tell you some things, running accessories/terminal and entering the command lspci will tell you other things. If you want a lot more, the commands:
sudo lshw >myconfig.txt
gedit myconfig.txt 
will give it to you.

Ubuntu runs fine with 512 MB of memory.

---

