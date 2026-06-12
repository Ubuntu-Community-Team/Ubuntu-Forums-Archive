---
title: "Built in Webcam not recognized on 9.04 Install"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Lupgaru on 2009-08-15
Just installed 9.04 on a new Gateway Laptop with a built in webcam and mic. Works fine in Vista on this dual boot but cannot find it in Ubuntu.

Gateway Model M-7315U
4GB Ram
Intel Pentium dual core 2GHz
1.3 mega pixel webcam with built in mic

Anyone know how to get Ubuntu to recognize the webcam or do I need to install a package?

Thanks:(After adding "Cheese Webcam Booth" web worked perfectly!)  Thank You All!

---

### Post by MaindotC on 2009-08-15
Assuming it is connected via pci, post the output of lspci.  If it is built in using a different type of technology, like pcmcia, then post the output of lspcmcia, and so forth.

---

### Post by K. Hendrik on 2009-08-15
do you have the right software installed for using your cam? you could use cheese for example (Console: "sudo apt-get install cheese")

---

### Post by Lupgaru on 2009-08-15
> **K. Hendrik said:**
> do you have the right software installed for using your cam? you could use cheese for example (Console: "sudo apt-get install cheese")
You were right about "Cheese". Worked right after install. Worked so fast it surprized me. 
Thank You

---

