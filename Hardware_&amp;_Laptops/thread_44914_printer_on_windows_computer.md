---
title: "printer on windows computer"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by DarkManX4lf on 2005-06-28
i have a router which has two pcs connected to it and a xbox, one pc has a printer connected to it, when i used to use windows i could access that printer over the network and it would work...how would i do that here? the printer is still connected to the windows pc on the network....

---

### Post by DarkManX4lf on 2005-06-29
bump

---

### Post by FesterHead on 2005-06-29
Check out this thread:
[HOWTO: Print to a windows XP machine](http://www.ubuntuforums.org/showthread.php?t=32190)

---

### Post by DarkManX4lf on 2005-07-09
i tried that guide, and it doesnt work, i made sure i put in the right ip, and that i selected the right printer, and also put in the right share name and it wont print....the printer is turned on, and its connected via usb to the windows machine.  The ubuntu and windows machine are connected to each other thru a router...both the printer and the windows machine are turned on but it wont print.

---

### Post by asimon623 on 2005-07-09
I have a printer on ubuntu and I can print from windows. I could help you with that.

---

### Post by DarkManX4lf on 2005-07-10
thanks but i dont think that would help, my configuration is reversed, the printer is connected to the winxp machine, and i dont have  the space to put it near the linux machine...

anyone have any suggestions?

---

### Post by manicka on 2005-07-10
check your settings again.Step 4 of the how-to should do it for you, once samba is installed

---

### Post by DarkManX4lf on 2005-07-11
still doesnt owrk, i tried to redo step 4, and i checked my settings, i tried to put in my root user and pw, and the regular username and pw that i created during setup it is still not printing..

---

### Post by manicka on 2005-07-11
[QUOTE=DarkManX4lf]still doesnt owrk, i tried to redo step 4, and i checked my settings, i tried to put in my root user and pw, and the regular username and pw that i created during setup it is still not printing..[/QUOTE]
 You need to put in the username and password of the windows machine, not your linux machine

---

### Post by DarkManX4lf on 2005-07-11
[QUOTE=manicka]You need to put in the username and password of the windows machine, not your linux machine[/QUOTE]

hmm i'll give that a try, when the windows machine is on should i use the user/pass (for linux printing) that is currently signed on? or can i use any user name that is on that computer?

---

### Post by manicka on 2005-07-12
I would use the username and password of an account with admin priviliges

---

