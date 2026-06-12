---
title: "G++ installation problems"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by merrill541 on 2009-04-30
Hello everyone.
I have been trying to install g++ on my ubuntu by using sudo apt-get install g++ but whenever I do that I am pretty sure what happens is that the apt command does not see the two plus signs and tries to install or search for packages called g. Any suggestions?

---

### Post by _Purple_ on 2009-04-30
What is that output you get when you try to install?

---

### Post by merrill541 on 2009-05-02
Actually somehow it seems to have worked now. I think it was after I did the command sudo apt-get install update or something along those lines and then when I did sudo apt-get install g++ it works now. But before it was saying that it cannot find the package g.

---

### Post by _Purple_ on 2009-05-02
```
sudo apt-get update
```
This command updates package information. Glad to know that it worked. :)

---

