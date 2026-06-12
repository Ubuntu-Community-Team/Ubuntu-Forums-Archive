---
title: "Black screen after long time closed."
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by zaxer on 2005-05-21
Hi guys.

I got my Ubuntu installed in my Acer TravelMate 290 Laptot. 

Everythings right except when I let the laptop rest for a long time for example when I go to sleep.

I keep the laptop on for all night, about 8 hours with the screen closed. 
After that when I try to open the screen and continue working the screen wants to start but some stuff happens, some black screens and thats all. I have to reboot the system.

Do you know what happens?

Thanks guys.

---

### Post by ola on 2005-05-22
It feels like your computer goes to sleep during the night. Unfortunatley the sleep doesn't allways work as expected in linux... So my best advice is to either try to disable the sleep or to close the computer..

---

### Post by feloc on 2005-06-14
I have the exact same problem as zaxer. When I close the lid on my laptop for a few hours, and then try continue I only get blank screen.

If I have to "disable sleep" how do I do that?

I have HP Omnibook XE3 running Hoary.

---

### Post by Gandalf on 2005-06-14
i don't have this one, i have another weird one,
if i close the screen for almost 3 seconds or less and i open it, the PC hang up, rebbot is needed in this case
normally when i open the screen ubuntu password request come after 5-15 seconds of black screen but as i said if i closed it fro less then 5 seconds it hangs, if i leave it two days closed nothing happens
i have P Pavilion dv1071ea

---

### Post by jerome bettis on 2005-06-14
[QUOTE=Gandalf]i don't have this one, i have another weird one,
if i close the screen for almost 3 seconds or less and i open it, the PC hang up, rebbot is needed in this case
normally when i open the screen ubuntu password request come after 5-15 seconds of black screen but as i said if i closed it fro less then 5 seconds it hangs, if i leave it two days closed nothing happens
i have P Pavilion dv1071ea[/QUOTE]
 you can turn the backlight on with the command: sudo vbetool dpms on

you could map it to a function key or something or you could press alt f2 and type it

---

### Post by Gandalf on 2005-06-14
[QUOTE=jerome bettis]you can turn the backlight on with the command: sudo vbetool dpms on

you could map it to a function key or something or you could press alt f2 and type it[/QUOTE]
 but sudo require a password, and it's not that i can see something but without light, i can't seeee anything, black only

---

### Post by jerome bettis on 2005-06-14
very true i didn't think of that

personally i have the whole password thing turned off.  yeah yeah i know security blah blah save it i don't care.

i believe it is possible to allow certain programs to be run without root access using the sudoers file.  you should probably look into that.

---

### Post by aycee on 2005-06-16
ctrl-alt-f7 to get your X screen back

---

### Post by Gandalf on 2005-06-17
[QUOTE=aycee]ctrl-alt-f7 to get your X screen back[/QUOTE]
 nope i already tried that too

---

