---
title: "2 simple question"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by Gandalf on 2005-05-06
Hello,
i'd like to know, is there a way to empty the swap partition, i have 1GB swap (RAM 512MB) it is full often i'd like to know if there's a way to empty it without rebooting (sudo swapoff -a && sudo swapon -a don't work)

another question, is there a way to make the laptop hibernate when the battery is 0%? it is turning off (hard shutdown, like reboot -f)

thanks

---

### Post by nad on 2005-05-06
I think a better question is; Why is your swap partition being so heavily used?

As to hibernating when you have no battery power: The computer needs to get juice from somewhere.

---

### Post by oracle2025 on 2005-05-06
Linux takes care of any Memory Management Issues, there's no need for the user to care about.

---

### Post by Gandalf on 2005-05-06
[QUOTE=oracle2025]Linux takes care of any Memory Management Issues, there's no need for the user to care about.[/QUOTE]
 well no, yesterday i was developping with Zend Studio have A LOT of other programs opened ans was tired didn't even notice that it's slow, slept, woke up the morning found that AMSN has generated a bug report and closed and was too slow my PC, open the console there was 2 MB left of SWAP 0 in RAM
i closed every single piece of software i gained 14MB of RAM nothing from SWAP!!!
so i rebooted
now i have Zend open firefox, thundebird amsn with some chat wndows, one console, iglooFTP and 2 nautilus
i have 75% used of RAM and 49% of swap!

---

