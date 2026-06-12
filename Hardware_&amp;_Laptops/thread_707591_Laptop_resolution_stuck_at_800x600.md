---
title: "Laptop resolution stuck at 800x600"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by jwm93k on 2008-02-25
Greeting

---

### Post by jwm93k on 2008-02-25
Sorry, fat finger.....
I have installed Ubuntu 6 and 7.10 on various laptops from different vendors. Each install only leaves me with 800x600 resolution or lower. I looked at the xorg.conf file and the only resolution listed in this file is 1024x768. This does not even come up as an option when I try to select my resolution of my screen.
I have search the forums, but I have not found a solution that works. Should fixing my monitor be this annoying? I look forward to any help you can offer.
](*,)

---

### Post by jwm93k on 2008-02-28
Yes I am still hoping for an anwer, this year.......

---

### Post by jwm93k on 2008-03-03
Can any one see this question? I am getting no response whatsoever. Let me know you actually see this post please.

---

### Post by alexandru_sorin on 2008-03-03
[http://ubuntuforums.org/showthread.php?p=4447493#post4447493](http://ubuntuforums.org/showthread.php?p=4447493#post4447493)


try this:
sudo -s
sudo nvidia-xconfig
sudo init 6
sudo -s
sudo nvidia-settings
put your resolution, then "save to x configuration file" button


that's it

My problem is wirelees, install good driver, works 2 times ( first time was ok, after shutdown, stops working) after few reboot work again then stops. Seems to work when she want. Any solution will be apreciate. Everything work's in my laptop except wireless.

---

### Post by alexandru_sorin on 2008-03-03
System ACER Aspire 5520
AMD64 Turion 2GHz, GeForce7000M, 2Gb Ram, 250Gb HDD, Atheros 5007eg wireless card. Good driver, work 2 times, them stops. Guess i have a problem with my mac number. Any sugestion?

---

### Post by alexandru_sorin on 2008-03-04
Done with wireless to. Install macchager package and change the mac adress.

---

### Post by jwm93k on 2008-03-09
Hello,
I have the NEOmagic display chip. I have reinstalled the drivers from synmatic. I have edited the xorg. config file. I changed the default display depth  from 24 to 12. I have added 1024x768 to the file for all depths. I have rebooted. I Still only get the 800x600 resolution selection. I have the option of 600x400, but this resolution is not even listed in the xorg.conf file. These are normal things called out by the general froums, but nothing works. Any more idea?

I don't know why someone put a wirelist plug in here.

---

### Post by acron1 on 2008-03-09
What is the native resolution of your monitor?
When you boot from the Live CD is it the correct resolution?

---

### Post by jwm93k on 2008-05-01
Hello,
Thanks for those who gave suggestions.
I had hoped that Ubuntu would bring new life to this old PC. I was wrong. Ubuntu will install, the sound and wireless will not work, and hibernate will not work, but the monitor resolution as a end game here. I guess the only thing I have left to do is figure out how to load windows on this old PC.

PLease consider this issue closed with no workable solution.

---

