---
title: "ubutu update disaster"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by ReignWolvas on 2009-02-17
ok ill start by first mentioning that i have NO clue when it comes to most things concearning computers and or the terminology used to describe even the most simple of things.

Ill just say whats happened and with any luck i cant get some assistance. 


I've been running an older version of ubuntu for ages now, and decided today to upgrade .

i opened my update manager ,went through the install etc etc. And it was 18 minutes to the point where it would start "cleaning up" when it froze . 

i waited ,and waited, and waited ....nothing so i did the only thing i could think of i rebooted .

now its locked me out of my desktop. The login menu has changed , looks newer and such but when i enter my password and name like usual it tells me my "home" does not appear to exsist. or something to that effect. other times ill put my username and password in and then it just goes to a blank orage screen . 

it reccomends running a failsafe or something , i tried one but i have no idea wtf im doing  ,seriously this is like alien to me. 

any idea what i should do ,step by step would be the best ^^'

---

### Post by dstew on 2009-02-17
What version of Ubuntu did you start with, and what version were you upgrading to? If you try to boot, do you get a grub menu? If so, have you tried to boot in recovery mode?

---

### Post by ReignWolvas on 2009-02-17
See idk what a grub is , thats why im having troubles i just dont understand. 

i tried running it in recovery mode but it doesnt seem to do anything ,just takes me back to the same login screen with the same issues.

i cant recall what version i was previously running but i updated the newest version via my update mananger.


uuummmm Ubuntu 8.04.2 

now i have 3 recovery modes to choose from , 

ubuntu 8.04.2 kernel 2.6.24-23-generic (recovery mode)
ubuntu 8.04.2 kernel 2.6.22-15-generic (recovery mode)
 ubuntu 8.04.2 kernel 2.6.22-14-generic (recovery mode)

does it matter which one i select ?

---

### Post by Bablefish on 2009-02-17
Yes this happens..a lot more than whatever is mentioned here (you should check out the Doctor Who forum) so much so the people there reccomend you do not update, but instead do a clean install.

---

### Post by ReignWolvas on 2009-02-17
how do i do a clean install?

i hope that doesnt invlolve an instillation disk, my cd drive is toast

---

### Post by hockman5 on 2009-02-17
When you first turn on your computer and it gives you a menu of choices, that is called grub, it is a boot manager. What does your screen say when you first turn it on? By the looks of what you already said, it looks like you were on 8.04 and still are. Maybe just the kernel was updated in which case you should be able to boot your system to the old kernel and have your original system still run. Let me know what your boot window says when you first turn on the computer.

---

### Post by ReignWolvas on 2009-02-17
well it gives me the option to press esc which takes me into the menu where i can access recovery mode etc etc . after that if i dont press esc it just goes through the normal stuff black screen white text . 

i JUST managed to get to my desktop ,but its on safe mode or something, no internet access


oh i forgot to mention , when i run safe mode i get the option to "repare broken packages"

it goes through some more text and concludes with this msg saying 

"dpkg was interrupted you must manually run dpkg -- configure 'a to correct "

idk what that means but mabye its the problem

---

### Post by dstew on 2009-02-18
If you have a desktop running, open a terminal (Application --> Accessories --> Terminal) and enter on the terminal command line```
sudo dpkg --configure -a
```See if that helps. If you get more errors, post back.

---

### Post by Michel Tatoute on 2009-02-19
> **ReignWolvas said:**
> well it gives me the option to press esc which takes me into the menu where i can access recovery mode etc etc . after that if i dont press esc it just goes through the normal stuff black screen white text . 

i JUST managed to get to my desktop ,but its on safe mode or something, no internet access


oh i forgot to mention , when i run safe mode i get the option to "repare broken packages"

it goes through some more text and concludes with this msg saying 

"dpkg was interrupted you must manually run dpkg -- configure 'a to correct "

idk what that means but mabye its the problem

that mean you got some problem while updating. Package database is not properly closed and need some repair.

Your first objective will be to obtain a console. Either you succeed a graphical login, then you open a console as described in other post, either (a second choice solution) you boot in single user mode.

To do that, when you are in grub menu, go to the failsafe entry is it exist, and edit it (press 'e') and add the word 'single' at the end of the boot line (the one beginning with linux....). Then you boot (probably using key 'b') and after some init you can obtain a pure text login. log in if necessary, become superuser (sudo -s) and type the command required for the package database like this

dpkg --configure -a 2>&1 | tee -a /root/messages

do not make typing error, specifically do not add nor remove spaces!

Michel.

---

