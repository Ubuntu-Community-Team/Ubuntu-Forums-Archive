---
title: "Can't suspend to ram"
date: 2008-10-16
forum: General Help
---

### Post by reffu on 2008-10-16
I built my desktop computer from scratch so i can;t tell you the make and model if anyone was going to ask. Anyway I cant suspend to ram. I dont know if this is a hardware inability or a software error but. there is no sleep feature in my shutdown box. I have: lock screen,hibernate,log out,switch user, restart, and shutdown but no suspend to ram. when i use the command pmi action suspend i get this:
 
method return sender=:1.9 -> dest=:1.56 reply_serial=2
   int32 1
and when i use the command sudo /etc/acpi/sleep.sh
it skips to the next line and nothing happens.

can someone help me figure out the problem. 

thanks,

reffu

---

### Post by kerry_s on 2008-10-16
you'll have to go down the list till you get something we can work with.

open a terminal and try these:

sudo hibernate-ram

sudo pm-suspend

sudo s2ram -f


i think that's all of them, make sure your using the right vid driver.

any output will help us help you.

also check your bios, make sure the power/sleep is set to s3 not s4.

---

