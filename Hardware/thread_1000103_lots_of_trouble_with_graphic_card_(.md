---
title: "lots of trouble with graphic card :("
date: 2008-12-02
forum: Hardware
---

### Post by valentt on 2008-12-02
Hi,

I have issue with NVidia GeForce 7300 - won't start X unless using vesa driver :(

Ubuntu is a bit older 7.04 but I can't upgrade so please if you have some tips how to troubleshoot this problem on Ubunut 7.04

I have now Nvidia 7300 with latest nvidia drivers when X start to load monitor just goes to stand by, everything works because I can still login through ssh and ping the box  - so it is not frozen.

Please help me because I'm going nuts... 

Here is my xorg.conf s below so please yell if you see something obviously wrong :)
[http://paste.ubuntu.com/79477/](http://paste.ubuntu.com/79477/)

and also yell if you see error messages in this X.org log file that would point to some obvious error:
[http://paste.ubuntu.com/79478/](http://paste.ubuntu.com/79478/)

Thank you in advance,
Valent.

---

### Post by hotballz87 on 2008-12-02
is it a new card?
sometimes you have to setup the computer to run the card from the bios, say if you were switching from an onboard to a pci-e card, you have to tell the bios to use a pci-e card, and not onboard.

i had that problem on my media center box when i upgraded from onboard to a new card

---

