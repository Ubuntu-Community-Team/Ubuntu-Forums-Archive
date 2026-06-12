---
title: "name resolution"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by abarai on 2005-01-18
I just installed Ubuntu, and there is an error ocurring at the boot of the computer. It says:
*ror: temporary failure in the name resolution
How can I fix this? :confused:

---

### Post by cabu on 2005-01-18
I 'assume' this is during synchronizing with the ubuntu ntp (Network Time Protocol) server. I assume this since I saw the error when I first installed ubuntu. Since I'm generally not connected to the internet while booting (dial-up), I just deleted the symlink /etc/rcS.d/S51ntpdate (verify the actuall number, as I'm not at my ubuntu box).

---

### Post by abarai on 2005-01-18
I should have soon my internet connection on ethernet,  so if I understand correctly, i won't have this problem then. Thx :)

---

### Post by cabu on 2005-01-18
Better yet look at this [thread](http://www.ubuntuforums.org/showthread.php?t=2706&highlight=ntpdate)

I learn something new everyday  :-?

---

