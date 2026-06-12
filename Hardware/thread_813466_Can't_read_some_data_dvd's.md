---
title: "Can't read some data dvd's"
date: 2008-05-30
forum: Hardware
---

### Post by tochtli on 2008-05-30
Hi, this is my first message in this Ubuntu forum...
I have a problem in my desktop with Ubuntu, i have a LG DVD rewriter model: GH20 LS10.
My problem is that when i try to read some dvd's it just don't mount the unit, i have tested the unit in windows and it read just fine, and the dvd's i can read it in another machine (a laptop) with the same Ubuntu version... i have tried with Ubuntu 7.10 and 8.04 and with the desktop i have the same problem. What i can do to solve my problem? please help me.
Thanks in advance.

---

### Post by abhiroopb on 2008-05-30
Welcome to the world of Ubuntu! :)

Let me see if I understand correctly, is it only certain DVDs that don't work? Or can you not read ALL dvds? Also have you tried the CDs? Are the DVDs any special type? Perhaps  you're LG model is defective or can't read a certain type (e.g. DVD+R).

---

### Post by tochtli on 2008-06-04
Hi there, sorry for not answer fast. i have been very busy in this end of semester (school).
Yes you are absolutely right i cant read some kind of data dvd's with  cd i have not problems. I have to say this... between the dvd's that i can read and the ones i can't read i does not change even the type all are dvd-r (samsung pleomax) the only thing that it change its the time and the program where i burn it. Like i say, the problem is not in the hardware because in windows XP i can read with no problem at all.
sorry again for the delay.

---

### Post by tochtli on 2008-06-04
Just one example to make this clearer. I have like 30 DVD's with my backup of music (this were burned from time to time). i have tried to pass it to a HD for more commodity and i can pass the DVD from the number 1 to the number 19 but the 20 and far (i don't know if this writes like this or "onwards" sorry for my bad english) i can read. I hope this example help's making this problem clear.

---

### Post by abhiroopb on 2008-06-04
Did you burn them using the same burner/settigns etc? What would you say is different between the one's that work and the one's that don't work?

---

### Post by tochtli on 2008-06-04
Ehh :confused: i think so. It were burned in the time when i were using windows xp like primary OS, if i remember all well, the program was cdBurner Pro XP there is a slightly possibility of one or two were burned in Nero, but i doubt about it. i stop using nero a long long time ago.

---

### Post by abhiroopb on 2008-06-04
Ok so explain what happens when you put int he ones that WORK and the ones that DON'T work. When you put in the ones that work, it should "mount", show up on your desktop (as a CD icon), and the directory should open.

---

### Post by tochtli on 2008-06-04
Ok :)

When i insert into the DVD recorder the DVD that work, like you say, it shows the icon whit the cd, and i can open it and everything works pretty good it mounts it and unmount it with no problem

But when i insert one DVD (the one that dont work) the unit make all the reading or something like that protocol and thats all, it does not mount any DVD, if i go to the desktop icon (equipo, because its in spanish) and i make double click in the DVD unit, then it show me a message "It could not mount the place. there is not support in the unit" and this is the same message that if i were not have any dvd in the unit.

---

### Post by abhiroopb on 2008-06-04
open a terminal and type the following: 

sudo mount /dev/cdrom /media/cdrom0

then brows to /media/cdrom0 and see if you can see your data

---

### Post by tochtli on 2008-06-04
Ok :confused::confused: this is absolutely odd. while i was writing the last messages, i was doing the marker by the computer actualization then this showed me to restart the machine so i do that, and when i was going to do what you tell me to do i put one of the DVD's that cannot read and surprise, i can now read those kind of DVD's it mounts it with no problems.

---

### Post by tochtli on 2008-06-04
If some of this information helps to solve similar problems. the actualization that i agree to do, where mostly the linux modules the last one (2.6.24-18).
If there is any way to get the complete list of applications that actualized today, please let me know to post it, this post maybe (i hope) help more people with a similar problem, once i read one person that has the same dvd writer and have also the same problem.

Also, I appreciate the help that abhiroopb give to me. THANKS alot i hope that in the future i could help like you.

---

### Post by abhiroopb on 2008-06-04
Glad its working. Restarting often clears up a LOT of issues!

---

