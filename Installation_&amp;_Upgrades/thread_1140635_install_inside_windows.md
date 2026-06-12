---
title: "install inside windows"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by czarg on 2009-04-27
Hello - I've been slowly migrating and trying UBUNTU - Live CD - Installed on my laptop (new hd).. and now I'm attempting to install 'install inside windows' option on CD v9.04
I'm in windows I place CD in and select the button install inside windows.. it asks series of questions - name / password / choose 17 MB and next.. it copies files and completes normally asking me to reboot or manually.  I select reboot.  My system boots back into windows xp like normal.  Thats it.  I can see a umbuntu directory on my hard drive.. but what am I missing? is there supposed to be another step? 

Any help?

George :)

---

### Post by Partyboi2 on 2009-04-27
Hi George, check that there is an entry for ubuntu in your c:\boot.ini file.

---

### Post by czarg on 2009-04-27
Yes this statement is in the boot.ini

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect
C:\wubildr.mbr = "Ubuntu"

Regards George

---

### Post by Dr.Vista on 2009-04-27
When you boot your computer up, do you get options of loading Ubuntu and Windows XP?

---

### Post by czarg on 2009-04-27
none - it just goes right into xp.... weird...
:confused:

---

### Post by czarg on 2009-04-28
*UPDATE - Figured it out.. just placed a timeout=10 line in the boot loader section so that I had the option...

*bump

full ini

[boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect
C:\wubildr.mbr = "Ubuntu"

---

