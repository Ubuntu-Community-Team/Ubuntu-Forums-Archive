---
title: "[SOLVED] Network Scanner"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by blingo on 2008-03-15
Hello
I have an HP Laserjet 3055, that can be used as a printer and as a scanner.
I connect to it using Ethernet.

While The printing part worked in seconds, I don't know how to make it work as a scanner.
Any Ideas?

Have a nice day! :-)

---

### Post by linuxwizard on 2008-03-15
Have you installed Sane ?
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

[http://tldp.org/HOWTO/Scanner-HOWTO/index.html](http://tldp.org/HOWTO/Scanner-HOWTO/index.html)

---

### Post by oldsoundguy on 2008-03-15
According to Google, the scanner can only work on the computer where it lives without adding some additional hardware.  From that same search it seems that such hardware is NOT cheap.  I may be in error on this, but it would behoove you to spend some time searching for a solution on Google, as the problem is the fact that the scanner sends a signal to the computer whereas a printer GETS the signal from the computer.

---

### Post by blingo on 2008-04-03
Problem Solved!

Thanks guys,
xsane didn't worked at first, 

With your help got to:

[https://wiki.ubuntu.com/HardwareSupportComponentsScannersHp](https://wiki.ubuntu.com/HardwareSupportComponentsScannersHp)

and from there to

[https://help.ubuntu.com/community/HpAllInOne#head-69e8ef592cf6197261fbe772a5eaeb1e30d2df5c](https://help.ubuntu.com/community/HpAllInOne#head-69e8ef592cf6197261fbe772a5eaeb1e30d2df5c)

followed the instructions of the last one, and now both scanner and printer work.

I'm very pleased with that :-)

---

### Post by linuxwizard on 2008-04-03
Good to hear that you got your scanner/printer setup and working. Please mark thread as SOLVED. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

