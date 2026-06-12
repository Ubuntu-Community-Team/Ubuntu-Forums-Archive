---
title: "[SOLVED] Login Window Missing on System"
date: 2008-08-23
forum: General Help
---

### Post by Gow524 on 2008-08-23
Hi, I was having a "Greeter login 'Application Crashing" during boot and when I decided to customized my log in screen, but I got some help from the forum and manage to get into my desktop via the command line.  What I was told do was:

$ killall gdm

$ sudo killall gdm
follow by

$startx

My only problem now, is that once I am on the desktop, I no longer have the  "Login Window" able under the System Menu so that I can disable the faulty greeter application and set the default Log in greet.  Also, the only way to exit out of the system, I have to log off  and then hold the power button.  

Do I have to re-install Ubuntu?

---

### Post by Garratt on 2008-08-23
nope, i had this same problem... ill try and find a solution.
hmm sorry i can not find it, basically there was a post in a login screen theme on gnome.look that pointed to a fix for it, basically it was getting into config file for login and removing whatever custom theme you put in there via commands. but yea... i used another comp to find the solution so now i can't find it...

EDIT: wait i lied....

I wrote it down in my notepad...

1. Press CTRL ALT F1 - soon as you would be at the part where normal login screen appears.

2. login as root.

3. now edit gdm config, type:   sudo nano /etc/gdm/gdm.conf

4. scroll down untill you see: Greeter=/usr/lib/gdm/gdmgreeter

5. now change that to:  Greeter=/usr/lib/gdm/gdmlogin

6. now restart it:  sudo /etc/init.d/gdm restart

wait a cpl mins....now cause i dunno how to reboot just hit the reset button on your comp. and you should be fine.

---

### Post by Garratt on 2008-08-23
let me know if it works or not

---

### Post by Gow524 on 2008-12-13
Problem is fix. I just re-install Ubuntu from scracth.

---

