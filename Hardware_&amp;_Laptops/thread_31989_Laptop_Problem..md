---
title: "Laptop Problem."
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by jleaman on 2005-05-05
Ok so I’m new to this Ubuntu stuff, BUT you guys hooked me on it from mandrake. So far it is a great os and nice layout easy to setup and use. I like it. But i have a small problem. I have a Dell laptop PIII 1 gig with speed stepping i just put a new drive in it a new 40 gig hard drive with 256mb ram onboard audio and video every thing works just perfectly but the speed stepping part. When I’m using it and a application is opened it goes from 732mhz to 1gig but after dro9pping back down to 732 it freezes momentarily. Id like to fix it because it does it so much and i hate it because the machine locks up for that split second. I was reading on here and found a topic of changing the speed step to be full power on but i cant find it now i looked for a straight hour. Can some one help me please. ?

---

### Post by arbearce on 2005-05-05
Check this post out [http://ubuntuforums.org/showthread.php?t=21370](http://ubuntuforums.org/showthread.php?t=21370)

I use KDE and KLaptop lets me configure how to run it, I don't know Gnome has something like KLaptop or not.

---

### Post by jleaman on 2005-05-05
Thanks man.. now to figure out how to do this. : O ) 

Jason

---

### Post by arbearce on 2005-05-05
First I would suggest doing

```
cp /etc/init.d/powernow /home/yourdir/backup/
cp /etc/acpi/power.sh /home/yourdir/backup/
```

then it should be as easy as

```
sudo cp /downloaddir/powernowd.txt /etc/init.d/powernow
sudo cp /downloaddir/power.sh.txt /etc/acpi/power.sh
```

Reboot and should be working

---

### Post by jleaman on 2005-05-05
[QUOTE=arbearce]First I would suggest doing

```
cp /etc/init.d/powernow /home/yourdir/backup/
cp /etc/acpi/power.sh /home/yourdir/backup/
```

then it should be as easy as

```
sudo cp /downloaddir/powernowd.txt /etc/init.d/powernow
sudo cp /downloaddir/power.sh.txt /etc/acpi/power.sh
```

Reboot and should be working[/QUOTE]


Dont i have to remove the .txt from the end of the file ?

---

### Post by arbearce on 2005-05-05
I didn't when I played around with it. 
You should be sort of copying and renaming the file when you do that. now if it was something like 
```
cp file.something /here/. 
```
Then it should copy it with the orginal file name but when you give it a file name in the destination end it will copy or copy over.

---

### Post by jleaman on 2005-05-05
Sorry for my stupidness i see right here. 

sudo cp /downloaddir/powernowd.txt /etc/init.d/powernow
sudo cp /downloaddir/power.sh.txt /etc/acpi/power.sh 

it will change it from .sh.txt to .sh : O )


I'll try this asap when i get home i hope this fixes this problem.

---

### Post by jleaman on 2005-05-06
ok  i copied these files to these dir's and rebooted and my cpu still changes from 731 to 999 / 1gig what can i do to change this ? Any one got another soloution ?

---

