---
title: "Dell Inspiron 1501 doesn't reboot with Envy drivers"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by flip79 on 2008-03-24
Hello, and sorry for my english.

I followed instructions on:
[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html](http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html)

And so I installed Envy... that installed automatically newest drivers from ATI for the Xpress 1150 graphic board that I have on my Dell Inspiron 1501. They works very well, but now my laptop doesn't reboot anymore. X11 quits and I get a black screen.

Some comments of the post report this problem, but no solution is suggered. What I can do?

Thank you in advance!!!

---

### Post by flip79 on 2008-03-25
Up :KS

---

### Post by overdrank on 2008-03-25
> **flip79 said:**
> Hello, and sorry for my english.

I followed instructions on:
[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html](http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html)

And so I installed Envy... that installed automatically newest drivers from ATI for the Xpress 1150 graphic board that I have on my Dell Inspiron 1501. They works very well, but now my laptop doesn't reboot anymore. X11 quits and I get a black screen.

Some comments of the post report this problem, but no solution is suggered. What I can do?

Thank you in advance!!!

Hi and have you tried to reconfigure you xorg  with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` You can use the keys ctrl,alt,F1 and this will bring you to command prompt.

---

### Post by flip79 on 2008-03-25
Hello and thank you for your answer.
I tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and reboot worked, but just because xorg.conf reverted to use "ati" driver. 

Then I reinstalled the proprietary driver with Envy (fglrx) and the problem came back :(

CTRL+ALT+F1 does nothing... the screen is still black and I've to turn my PC manually, keeping the power button pressed :(

---

