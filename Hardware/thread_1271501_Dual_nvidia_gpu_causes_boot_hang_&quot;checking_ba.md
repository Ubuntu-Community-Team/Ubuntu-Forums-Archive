---
title: "Dual nvidia gpu causes boot hang &quot;checking battery state..&quot;"
date: 2009-09-20
forum: Hardware
---

### Post by rette7mich on 2009-09-20
ok to start things off, i am very new to ubuntu. i took a linux class last year but we used fedora core 8, and i expected them to be practically the same but i've found that this is not true.

the problem...
  ok so i am running two nvidia geforce 9400 gt graphics cards, and i am running these on an intel based x86 64bit system using ubuntu 9.04. my intallation went fine and i intalled all of the updates, then i tried to install the reccomended graphics driver for my gpu's (version 180). the installation finished and i was prompted to restart. upon restarting my boot hangs at "checking battery state... [ok]" which i found odd being as how i am running a desktop pc. when this happens i am still abe to access other terminals and operate as root, but i just simply dont know how to fix this problem.

i tried looking for the file to edit the boot processes, but i couldn't find exactly what i was looking for (mainly checked event.d)
tried to manually install the driver from nvidia but couldnt because the driver must run in runlevel 3 and i recently discovered that 2-5 in ubuntu are all full multi-user so i couldn't end my X server session.
tried both offered versions of drivers offered by hardware drivers and both gave me the same result.

after trying each of these, i was clueless and still stuck at boot, so i would reinstall ubuntu.  also tried ubuntu 8.04.3.

but then... i tried disconnecting one of my gpu's and installing the driver, AND IT WORKED!!!  i had read on some other forum that it was some conflict with having 2 so i tried it and bam, it works.

so why is it ubuntu or linux wont support my multiple gpu's?? is it because of their SLI capabilities? IRQ (at least in windows its called this) problems?  anyone have a clue or any kind of insight for me??  i have actually seen a lot of people on other forums with this same exact problem so i think its time for an answer. 

any help would be greatly appreciated!!!
i want to run all 4 monitors again =D

p.s. sorry i have no log files to submit but this happened on versions of ubuntu that i have since replaced with the exact same version.

---

### Post by Wintaru on 2009-09-27
I'm having the same problem with my install.  Happened after I enabled the restricted nVidia drivers, now it stops at the Checking Battery State message and I can't boot into my desktop.

---

### Post by hpprinter100 on 2009-10-10
same here i have dual  9500gt...very annoying are their any drivers that wont cause this problem?

---

### Post by slamhound on 2009-10-15
See the following post for a fix:

[http://ubuntuforums.org/showpost.php?p=7452633&postcount=2](http://ubuntuforums.org/showpost.php?p=7452633&postcount=2)

This allows you to get both cards working, and you'll need to set up twinview for multiple monitors on the same card.  At first, you won't be able to drag and drop between monitors on different GPUs, but you can set up xinerama to do that.  But then once you have xinerama, I think that compiz won't work.  So I just left it with two monitors on one card with twinview and a separate monitor on a separate card, and I can't drag between the monitors on the separate cards.

---

### Post by rette7mich on 2010-09-17
this totally worked!!! i followed the instructions from the above post, even with some variations (was not a fresh installation, just uninstalled driver.)

so anyone else with this problem this should work for you!

i now have 3 compiz friendly monitors =]

Thanks slamhound!!!!!

---

