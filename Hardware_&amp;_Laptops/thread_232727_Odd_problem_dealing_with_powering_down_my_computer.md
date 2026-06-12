---
title: "Odd problem dealing with powering down my computer"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by pikakilla on 2006-08-09
This odd problem has started occuring within the past three days. I  seriously dobut it has anything to do with my OS (almost 100% sure of it), but whenever I power down my computer via shutdown, once it goes through its power down sequence, it turns back on. This happens when I use the manual power button as well at any point during the bootup etc. For obvious reasons google has turned up nothing (i get lots of windows xp my computer wont turn off errors) and ive tried everything that i have read in those areas (checking lan bootup/apm etc). Ive checked the fpio to see if there is a short causing it to boot up randomly (none as far as i can tell). I am thinking it has to deal with my power supply, but i dont know how to check and i have no idea where else to turn to for such an odd problem :(. Thanks for any replies

Asus NFORCE2
antec psu (about 3 years old)

---

### Post by skirkpatrick on 2006-08-09
Not sure if this helps but the machine I use for my server has an option in the BIOS to reboot the machine anytime it is shut down but still has power.  This is nice in a server in that if I have a power glitch it will reboot instead of waiting for me to push the button.

---

### Post by bigken on 2006-08-09
Hi check your bios settings things like boot from keyboard ect and dissable 1 at time to see which 1 is causing the reboot ;)

---

### Post by pikakilla on 2006-08-09
ive already checked all settings in the bios that would cause a remote bootup or alternate power on. it should only power up if i press the power button

---

### Post by bigken on 2006-08-09
I remember someone had the same problem before and it was the keyboard do u have another one to try it with ;)

also are you sure you dont have a sticky power button 

what is your mobo spec

---

### Post by pikakilla on 2006-08-09
Checked it, it said that it was disabled and power button is the only one to turn it on. I disabled the use of the power button and it still turned itself on after shutdown. It only does it after i shut it down or power it down via the power button. If i unplug it and plug it back in it will stay off. 

mobo nf7-s

---

### Post by bigken on 2006-08-09
I would try with every unpluged ie printers ect did u try another keyboard ?

---

### Post by pikakilla on 2006-08-09
My bad, i misread your message. Yes i just checked it with a new keyboard and tried both the ps2 port and usb port. The same problem occurs.

---

### Post by bigken on 2006-08-09
ok have you added any new hardware also what is your hdd setup 
i once had a machine with 2 sata drives but when I added a pci drive 
it made the machine reboot

---

### Post by pikakilla on 2006-08-09
ive had this current setup for about 1.5 years. There have been a bunch of power failures in the area and im wondering if that could have contributed to the power short. Im going to test with a bunch of stuff disabled in my bios (lan/parallel ports etc) and see if any one of them is the culprit
5 hdd's 
1 sata
4 ide
1 cdrom

---

### Post by bigken on 2006-08-09
I think your earlier coment about the PSU could be right one dont have a spare or an old one to swap it out with just to eliminate it failing that it sounds like a fault on the board :-k

---

### Post by pikakilla on 2006-08-09
well son of a bitch... it was the parallel port as far as i can tell. Im going to run a few more tests to make sure it stays off. My poor old board. Its been through so much hell, yet it still keeps kicking :)

---

### Post by bigken on 2006-08-09
pleased to hear you got sorted mate these things were sent to try us =D>

---

### Post by pikakilla on 2006-08-09
Yup. It was the parallel port. I reenabled all the other things and it shuts down cleanly now. Thanks for the help

*pleased to hear you got sorted mate these things were sent to try us*

Agreed, but thanks to this community I was able to solve this problem. This alone makes switching to ubuntu one of the best things ive done for my comp :) Once again, thanks for the help

---

### Post by bigken on 2006-08-09
thats what were all here for ;)

must ask do you run your unit though a surge protector ?

---

### Post by pikakilla on 2006-08-09
Yeah i do. We have a lot of power surges/slumps in the area so i sprang for a "battery backup" system. The problem with this battery backup is it does not act like a ups by any means, yet advertises itself as one but never explicitly states it is a ups, so whenever a power slump occurs (normally for one second, but its enough to interrupt power to electronics) it takes the battery backup a second to go into backup mode which completely negates any purpose to having the damn battery backup :( Im going to spring for a ups soon to aleviate any of these problems

---

### Post by bigken on 2006-08-09
dont blame you mate better safe than sorry ;)

---

