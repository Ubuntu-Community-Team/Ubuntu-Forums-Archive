---
title: "Nvidia GPU VERY HOT is this normal?"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by chronusdark on 2008-03-31
what is the normal running temp for a Geforce Go chip because if my sensors are reading correctly my GPU gets to 90 degrees celsius when playing games is this normal? my fan is running  i can hear it

---

### Post by jacob01 on 2008-03-31
i was wondering the same thing about what is a good idle temp and a high temp for a gpu, i have a geforce 8600gt over clocked and the most i have seen it get to was 60 but thats when i was running glx gears, i cant see it while playing a game. It probably gets higher but i cant see to record it. btw im using the nvidia x server settings program to view my temps

idle i get like 46-48 celcius  but mine is in a direct flow of air with an exhaust fan right above it.

the slowdown threshold is 115 for my card so at that point i guess it will under clock the gpu to let it cool off so i guess your safe but to me that seems like a high temp.

please give more info about your gpu like what series and im assuming it is a mobile version in a laptop right?

---

### Post by chronusdark on 2008-03-31
its a Geforce Go 7400 with TurboCache
and at idle its 62-65 degrees celsius
Compiz pushes it to the middle 70's 
and games up to 90's

i see no way to set my slowdown threshold

Edit: and yes a mobile chip

---

### Post by chronusdark on 2008-03-31
i also want to note that i get heat like this in windows as well but i dont know the exact numbers

---

### Post by sdennie on 2008-03-31
The temperatures for the 7400GS Go aren't terrible but they are a bit high.  If you can hear that the fans are running, you may want to use some compressed air on all the laptop vents to help improve airflow (it can make a surprising difference).  You could also take a look at the "nvclock" utility which, for some cards, allows you to control fan speeds.

---

### Post by chronusdark on 2008-03-31
i didnt see any fan controls in nvclock and when i tried to underclock my chip i screen went glitchy and i had to reboot

---

### Post by frodon on 2008-05-13
If fan control is supported by your card the following command will toglle you fan in automatic control mode :
```
nvclock -f -F auto
```

For the record i have a 7600GT (i don't use nvclock yet) :
idle temp 54C-62C depending on external temp
Gaming temp 64C-79C depending on external temp

---

