---
title: "problem with glxinfo"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by mondoUNC on 2008-01-14
I somehow messed up Gutsy so that Compiz is no longer working. It seems to be a problem with glxinfo. All my drivers are in order and Compiz was working yesterday so I don't know what i did. I'm  on an IBM Thinkpad R51, you can see [here]("http://ubuntuforums.org/showthread.php?t=651647&page=8") what steps I took in the Desktop Effects Forum.

```
mondo@mondo-ubuntu:~$ glxinfo | grep "direct rendering"
glxinfo: symbol lookup error: glxinfo: undefined symbol: glXChooseVisual
```

---

### Post by mondoUNC on 2008-01-15
Can anyone please help me? I've googled for help to no avail. I've tried reinstalling any thing GL related, openGL and some other things but nothing seems to have an impact. I'm guessing this has something to do with 3d rendering since it seems like compiz and Frets on Fire are the only programs affected. I don't want to have to reinstall ubuntu, but if its the only way to get Compiz back I will.

---

### Post by Sef on 2008-01-15
> mondo@mondo-ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

mondo@mondo-ubuntu:~$ compiz --indirect rendering
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option --indirect

What happens when you install the restricted drivers? (Check to make sure they are installed.)   System > Administration > Restricted Drivers Management  

(My XGL had be be reinstalled a couple of times.  Not sure why, but that took care of my problems.)

---

### Post by mondoUNC on 2008-01-15
Thanks for trying to help but i got impatient and just reinstalled.

---

