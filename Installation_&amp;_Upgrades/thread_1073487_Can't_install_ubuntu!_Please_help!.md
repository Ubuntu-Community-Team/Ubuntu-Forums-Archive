---
title: "Can't install ubuntu! Please help!"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by enkhuush on 2009-02-18
hi all, 
here is my problem,
when I booting from Ubuntu cd I got language selection, I select english, and after that i choose Install Ubuntu and after some cursor blinking there is 

Loading please wait...
Linux Ubuntu 2.6.27-7 generic #1 smp

bla bla

to run a command as admin use "sudo <command> ", 
see "man sudo_root" for details.

ubuntu@ubuntu ~$ 

now what I got to do? what should I type in command?
i tried startx command and it is said no screens found, 
by the way, my hardware is DELL optiplex, core 2 duo, 4gb RAMs, Nvidia 8500GT card, and so on. 
thanks in advance, i really stuck here.

---

### Post by brak3000 on 2009-02-26
I'm having the exact same problem. I tried to install it as well as just run it without changing anything, and both times I got stuck on this command line ubuntu@ubuntu~$

I'm using a Lenovo thinkpad T500, with an Intel core 2 duo processor. Please help! you would be solving at least 2 peoples' problems.

---

### Post by protodog on 2009-02-27
The blinking means that it's trying to detect your video card and probably wasn't able to do so successfully.

So doing startx won't work because your Xorg configuration isn't properly configured.

Your best bet is to go into /etc/X11/Xorg.conf and try to figure out your video card settings there. It shouldn't be too hard if you know your video card chipset.

If you are still having problems, I recommend posting your Xorg.conf here.

HTH

---

### Post by booshire on 2009-02-27
Have you tried doing a safe install, or even a text install? Your VC may be Vista enabled, which means maybe in linux. Text install and find out if driver exists (or install driver before install starts with the F* keys)

---

### Post by mperry on 2009-02-27
Be sure you follow the advice for the graphics chipset on the thinkwiki website for the T400. I just did a Ubuntu 8.10 install on my new t500 and got trapped by kernel panics and not mounting the root FS when the install finished. There are fixes for it all but it takes a bit of patience, chrooting, and retrying. With a fully updated 8.10 32bit, acpi events occur correctly and things seem pretty good. You have to monkey with the atheros or madwifi drivers though so be prepared for that too. I have on and off again issues with the card not coming back after a hibernation or suspend event. For me, I just remove the ath5k module and re-insert it.

Good news is that the t500 performs very nicely but it just takes a while to get there. I have virtualbox working on a separate desktop running the company required email solution.

---

### Post by brak3000 on 2009-03-02
Actually, I figured it out from the thinkwiki page. It said in the BIOS to change the display display type to a set type and disable the OS detection of the display. After that it worked fine. Thanks for all your help though!

The link is here, for anyone else having this problem:
[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400)

---

