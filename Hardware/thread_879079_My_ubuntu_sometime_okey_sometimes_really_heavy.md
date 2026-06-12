---
title: "My ubuntu sometime okey sometimes really heavy"
date: 2008-08-03
forum: Hardware
---

### Post by aisar190 on 2008-08-03
Greeting everyone,
   Before i mention my problem i would like you all the brainy out there know my laptop spec... :)...im using intel centrino 1.8ghz with 2gb ram...old laptop thou....12" screen dell d400 with 40gb hard drive....
   i split the hard drive to windows and ubuntu....i hardly used my windows now...its faster to used ubuntu.....my problem is...this fast performance in ubuntu is not constant...sometime its really slow...while i only open my firefox with 4 tabs open...i just wondering why is this happening...
   and how can i check my system information like windows..when we click on properties at my computer icon....there is a system info about our proc and ram and etc...how can i do that in ubuntu ?.....sometime it feels the ubuntu is running something on the background....how can i check what is the thing were running on my ubuntu ?....please anyone have any idea ?.....
thx in advance....god bless you all... :)

---

### Post by phidia on 2008-08-03
To view all processes open a terminal from Applications > Acessories > Terminal
and enter "top" To view processes currently running enter "ps".
Hope that helps.

---

### Post by Frem on 2008-08-03
You can also use System > Administration > System Monitor to look at running processes. It may be somewhat easier for you to use.

Try to corrilate the slowness to actions. Does the computer become slow when you visit a flash site, for example? Or perhaps every 10 minutes when Evolution checks for email?

---

### Post by aisar190 on 2008-08-04
i found the source of the problem....its my firefox....when i closed my firefox...my processor is running at 600Mhz instead of 1.8Ghz when firefox is open.....is firefox resource hungry  ?....i opened 3 tab that time...nothing streaming....

---

### Post by mikjp on 2008-08-04
> **aisar190 said:**
> i found the source of the problem....its my firefox....when i closed my firefox...my processor is running at 600Mhz instead of 1.8Ghz when firefox is open.....is firefox resource hungry  ?....i opened 3 tab that time...nothing streaming....

Something wrong with your power management settings? Opening firefox should not change the running speed of the CPU.


Greegints,

mikko

---

