---
title: "compiz doesn't work"
date: 2008-07-12
forum: General Help
---

### Post by bobetko on 2008-07-12
**I can't enable compiz.**


**I tried compiz-check and all I get is an error:**

bob@ubuntu:~$ ./compiz-check
./compiz-check: line 1: --00:27:51--: command not found
./compiz-check: line 10: unexpected EOF while looking for matching `''
./compiz-check: line 12: syntax error: unexpected end of file

**When I just run compiz, I get this:**

bob@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0611 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

**Ubuntu 8.04, 2.4Ghz Quad, 2GB RAM, 8800GT Nvidia with dual scren**

Thanks

---

### Post by sayakb on 2008-07-12
Install the latest envy: [http://lunapark6.com/envy-easy-way-to-install-nvidia-drivers-in-ubuntu.html](http://lunapark6.com/envy-easy-way-to-install-nvidia-drivers-in-ubuntu.html)
Then do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

For compiz-check to work, you have to download it from here: [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

---

