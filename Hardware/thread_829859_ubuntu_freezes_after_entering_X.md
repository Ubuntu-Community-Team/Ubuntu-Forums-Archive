---
title: "ubuntu freezes after entering X"
date: 2008-06-15
forum: Hardware
---

### Post by cravonic on 2008-06-15
I have an aspire 2023wlmi laptop with a radeon 9700 mobility.
I commited a mistake and deleted the folder /var/log/, after some time it started freezing.
I tried the recover mode and reconfigured all the packets and reinstalled some packets with the command dpkg-reconfigure -a.

Now I have a problem after entering in X, passed some time (random), X freezes, the mouse is left unfrozen and moves, the keyboard gets stuck.
I tryed reinstalling xorg, reconfigure, install envy,etc...
Someone have a solution for this problem?

thanks in advance

---

### Post by Odrodzona-Sarmacja on 2008-06-15
reinstall the os.

---

### Post by briggella on 2008-06-15
You could try recreating the /var/log directory and giving it permissions of 755 by running *sudo mkdir /var/log* and *sudo chmod 755 /var/log*. Then restart X and see if it can recreate the log files. If it cannot write to the logs, it will seize.

---

