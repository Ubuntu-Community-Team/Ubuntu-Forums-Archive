---
title: "Help me in installing the software.."
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by aprashanth on 2009-09-11
I am trying to install a software.. called Rsoft..
Too start the installing process it requires me to copy the file into the home directory.. by binary format.. 

when I am giving the command

scp -rf media/cdrom0/Rsoft_LINUX/ home/tsrinu/Desktop
there is nothing happening.. why is this...please help..

---

### Post by realzippy on 2009-09-11
try again with:

cp -r /media/cdrom0/Rsoft_LINUX ./Desktop/

---

### Post by aprashanth on 2009-09-11
ya thank you it worked..

---

