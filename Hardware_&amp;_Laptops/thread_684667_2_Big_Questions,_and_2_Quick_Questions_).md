---
title: "2 Big Questions, and 2 Quick Questions :)"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by sumfight on 2008-02-01
I have a Dell lap top I just put ubuntu on for the first time.  I downloaded the iso and installed it on my computer.  Everything seemed to be going fine but now here are my two major problems.

1.  When I start my computer up, all I get is a blank screen, I have to hit Ctrl + Alt + F1 to make the screen come up to load ubuntu.(found this out through forums) but I wanted to know if that is normal?

2.  The add remove programs(applications) does not work at all.  It looks like it is downloading new one's from the net, but it does nothing at all.  I see a lot of other people have this problem as well, I tried some different ways to fix it but can't seem to, do you know any ways that would work to fix this problem?

3.  How do I install ubuntu again if I want to on the same computer, you know like clear my HDD and start over again.

4.  Also, is there a way I can still do my ghost restore(windows) because I have a dell 4600 laptop, and when i would press Ctrl + F11 it used to ask me if I wanted to restore it.

Sorry for all the questions, but your help will mean a lot to me :).

-Cody

---

### Post by murmel on 2008-02-01
3. Just boot from the ubuntu cd again and re-install it. :)

---

### Post by diwas on 2008-02-01
Well there is a file named usplash.conf in this location : /etc/ where the boot screen's size is recorded. By default, the size is i think 1280*1024. But some computer cannot accomodate this resolution so you have to change the resolution according to your system. To do this type this in the terminal:
sudo gedit /etc/usplash.conf
then a text editor opens where there are x= and y= values are set. Insert the resolution your monitor supports. And then save it (Ctrl+S).
Then close the text editor and in the terminal type the following:
sudo dpkg-reconfigure usplash
It will take some time and then you are done!!

Note: If this doesnt work too...set the resolution to the minimum like 640*480.

---

### Post by diwas on 2008-02-01
Talking abt re-installing, all i know is to format the drive and re-install it. Lol!!

---

### Post by sumfight on 2008-02-01
Cool, I will try this out :)

---

