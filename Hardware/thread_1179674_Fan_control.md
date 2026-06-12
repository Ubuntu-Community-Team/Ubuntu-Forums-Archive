---
title: "Fan control"
date: 2009-06-05
forum: Hardware
---

### Post by riminicat on 2009-06-05
Is there a way I can control the fan speed of my laptop on Ubuntu?  My laptops always had an issue with heat and I wondered if turning the fan up would help(along with blowing out the inside, which I did).

---

### Post by zuerston on 2009-06-09
I sure do hope you get an answer,I need it too,my HP AMD X2 Turion is hitting 60c with almost no load,fan rarely comes on,need way to control it. runnin Ubunto 9.04
**HELP US DUMMIES TOO!**
:p

---

### Post by Rickard_swe on 2009-06-09
Hey fellows ! 

60 celcius is good ,my CPU is 60-63 when i just surf on the webb.

And 70-79 in gaming. (pretty heavy games)  like half-life 2  (insurgency)  

Im new here.and im planing to install ubuntu on my lenovo thinkpad T60 . I going to install company of heroes,starcraft and maybe diablo 2 . And other WINDOWS program ,like my FAN control and drivers. Please.give me a link to a guide so I can install these softwares   =)

Greetings.Rickard.Swe  :D

---

### Post by AlexKpow on 2009-06-09
If it's an nvidia card, you can get nvclock from the repositories. The command to change the fan speed is:

```
nvclock -f -F [FANSPEED%]
```

So, to set it to 90%:

```
nvclock -f -F 90
```

---

### Post by riminicat on 2009-06-12
Dang, my fan doesn't support fanspeed adjustment.  According to HP the new bios update for the mother board does, but I don't have windows and the program is winflash...

---

