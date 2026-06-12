---
title: "Samsung N110: no brightness control is available."
date: 2009-12-21
forum: Hardware
---

### Post by Brodyaga on 2009-12-21
Hello. I have a problem with samsung n110 netbook: standard keyboard shorcuts for brightness control don't work in ubuntu 9.10, and control through power managment is also unavailable(there is even no slide bar or something like that). All "brightness" files under /proc/acpi/video directory(i have 5 subdirs there with identical content) contain only one line "<not supported>", that's why i can't map keys to brightness control through echo'ing to acpi device.

Did anyone installed ubuntu on n110 and how did you solve the problem? Screen is really dark, dammit =)

---

### Post by danielstrong52 on 2010-01-13
I have exactly the same problem. Well, not quite the exactly the same: luckily, it would seem, when I installed ubuntu my brightness was on max. Problem is that I am now stuck with about 4h battery life rather than the optimal 6h or so...

---

### Post by gillza on 2010-03-13
I had to reinstall a bare-bone version of XP 
( [http://www.liliputing.com/2008/04/install-windows-xp-on-mini-note-usb.html](http://www.liliputing.com/2008/04/install-windows-xp-on-mini-note-usb.html) followed wintoflash) and apply a BIOS update from [http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05012500&prd_mdl_cd=NP-N110-KA01US&prd_mdl_name=NP-N110](http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05012500&prd_mdl_cd=NP-N110-KA01US&prd_mdl_name=NP-N110)

Fn + up/down now works. 

Info found here: [http://www.uluga.ubuntuforums.org/showthread.php?p=8337513](http://www.uluga.ubuntuforums.org/showthread.php?p=8337513)

---

### Post by ectospasm on 2010-03-20
Thanks, this update worked like a charm for me!  Brightness control does indeed work now.

---

