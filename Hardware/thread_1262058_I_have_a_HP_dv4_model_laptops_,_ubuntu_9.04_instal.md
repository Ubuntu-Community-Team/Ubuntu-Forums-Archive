---
title: "I have a HP dv4 model laptops , ubuntu 9.04 installed properly but sound is not worki"
date: 2009-09-09
forum: Hardware
---

### Post by sellu@live.com on 2009-09-09
I have a HP dv4 model laptops , ubuntu 9.04 installed properly but sound is not working 
Pls how to get the clear sound in my laptop...........

---

### Post by Sam Lars on 2009-09-10
Check out if something the guide here helps:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by novistahere on 2009-09-11
The following commond fixed the sound problem on my HP DV4T.
Run the first line in the Terminal, add the second line to the end.

gksudo gedit /etc/modprobe.d/alsa-base

options snd-hda-intel enable_msi=1

> **sellu@live.com said:**
> I have a HP dv4 model laptops , ubuntu 9.04 installed properly but sound is not working 
Pls how to get the clear sound in my laptop...........

---

### Post by Mariane on 2009-09-11
When you speak about "clear sound", do you mean the sound is bad quality or is it not working at all? 

Mariane

---

