---
title: "Need help installing printer drivers"
date: 2011-08-29
forum: Hardware
---

### Post by mattdee132 on 2011-08-29
I have been trying to get my laptop to print to a fujixerox docuprint c2200 printer, but I am stuck.  I found a driver, but it is in .rpm format.  How can I get this working on Ubuntu?

---

### Post by Redblade20XX on 2011-08-29
.rpm file are designed for redhat like distros, if I'm correct while .deb are for debian like distros such as Ubuntu. In the .rpm there should be source code for building the printer driver so after extracting it, you'll have to build it manually.  To  try and keep everything automated, take a look at this: [https://help.ubuntu.com/community/RPM/AlienHowto.]("https://help.ubuntu.com/community/RPM/AlienHowto")

If that doesn't work and you will have to go in manually, take a look at this for manual extraction : [http://askubuntu.com/questions/52230/how-do-i-extract-a-rpm-file](http://askubuntu.com/questions/52230/how-do-i-extract-a-rpm-file)
After extracting the .rpm, there should be a readme file. Open it in a editor and follow the instructions!

Hopefully it all goes well with the automated method.:P

-Red

---

