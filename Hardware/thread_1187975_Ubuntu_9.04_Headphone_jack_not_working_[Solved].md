---
title: "Ubuntu 9.04 Headphone jack not working [Solved]"
date: 2009-06-15
forum: Hardware
---

### Post by davidv on 2009-06-15
[I]For the headphone jack not working problem I found a solution :

[/I]You have to add two lines to file /etc/modprobe.d/alsa-base

//add this lines
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto  position_fix=1 enable=yes

and restart laptop. I hope it helps.
I use Ubuntu Jaunty 9.04
My Laptop is an ASUS (A6000 series)

Copied from :
[http://ubuntuforums.org/showpost.php?p=4269068&postcount=6](http://ubuntuforums.org/showpost.php?p=4269068&postcount=6)

David V.

---

