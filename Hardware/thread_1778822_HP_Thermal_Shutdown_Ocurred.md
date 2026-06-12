---
title: "HP Thermal Shutdown Ocurred"
date: 2011-06-09
forum: Hardware
---

### Post by IDLCR on 2011-06-09
Hello! this is my first thread in this forum since im using ubuntu (2009)usually all my questions or problems get resolved in here but latley im having one that i cant find a possible solution 

Recenlty i bought a notebook (HP Pavilion g4-1064)since day 1 i wanted to install ubuntu which i suceed to without any problems my problem start when i restart the notebook a "Thermal Shutdown Ocurred" alert is displayed before i can even load the OS but the computer NEVER shutdown while in use even on heavy load, i installed lm-Sensors and it says my core temps are 47c idle to 67c under heavy load, which i think are normal temps because even under Windows 7 the temps are almost the same ( +- 2c )btw i think its good to say that when im under windows and i restart the pc the thermal shutdown ocurred display doesnt happen which makes me think that is something with Ubuntu doesnt communicate with the bios or something i have istalled the latest drivers and BIOS from HP support page but the error its still displaying

in resume
the notebook displays a Thermal Shutdown Error even when my notbeook its cool and never shutdown while in use its only when i restart the PC FROM ubuntu, from windows its ok

Hope i get explain ( Spanish its my native so i have some trouble explaining in english ) i really wish someone could help me, tough the Error Display its just .... an error its annoying Thanks

Sorry i forgot
Specs

core i3 2310m
intel hd Graphics 3000
320 hitachi Hdd
3gb 1333mhz Ram

---

### Post by [SiMON] on 2011-06-23
I'm having the same issue on a HP Pavilion dv7. Guess Ubuntu shuts down the computer in a way that the BIOS doesn't understand, and then the BIOS think that stop was because of overheating.

If anyone has a solution for that problem...

---

### Post by forubu on 2011-08-04
I'm still hoping this problem will be solved soon.
I need to disconnect my battery before plugging in the power and boot my computer. It's getting a little annoying...

I have tried setting acpi=off in grub.cfg to no avail. I have also searched the internet several times hoping someone have found a solution. But still no luck. :(

---

### Post by Oasu4g on 2011-08-26
Has anyone found a solution to this yet? I'm trying to fix this problem myself.

Kind regards,

Tim

---

### Post by jayfost on 2011-09-11
I have this problem on a HP Envy 17" 3D running Win7 and Ubuntu 11.04

---

### Post by ianjoneill on 2011-09-15
Hi, I have a HP Pavilion g6-1155sa and had exactly the same problem. I fixed the issue by updating the BIOS from F23 to F32 (The most recent version on the HP website.) (I found this out as I also had a problem where I could not put the laptop to sleep, so I thought the only answer could be updating the BIOS.)

Hope This Helps.

---

### Post by loboes41 on 2011-09-15
I also have this issue on an HP Envy 17 with 11.04 64 bit.

---

### Post by jayfost on 2011-09-16
> **ianjoneill said:**
> Hi, I have a HP Pavilion g6-1155sa and had exactly the same problem. I fixed the issue by updating the BIOS from F23 to F32 (The most recent version on the HP website.) (I found this out as I also had a problem where I could not put the laptop to sleep, so I thought the only answer could be updating the BIOS.)

Hope This Helps.



I already updated to the latest bios ffor my laptop which is f16 but i'm still getting the problem

---

### Post by Oasu4g on 2011-10-15
This seems to be more and more of a common problem. It looks like it's a firmware bug in older versions of Insyde BIOS. I flashed BIOS yesterday, upgrading it from F.0A to F.0F, and the problem sadly persists. I am running Windows 7 and Linux Mint 11 on an HP Dv7-4296nr.

---

### Post by IDLCR on 2012-02-13
ok, sorry for taking so long to answer and maybe you all have already solved it, the problem disappeared when i updated the bios, the last one from HP support page and now the problem is gone, F.52

---

### Post by loboes41 on 2012-02-13
How do you update the BIOS through Ubuntu?

---

### Post by IDLCR on 2012-02-13
i dont know, when i want to update the BIOS i dual boot windows, its the only way i know sorry:(

---

### Post by tulipán on 2012-07-20
my solution to the same problem (hp g62) is to lift the laptop and put it on a book, so it is still in a comfortable slopy position for typing and i'm giving the fan more air. i know this is NOT the kind of solution preferred here, but as long as i cant find a software/setting solution, i have to do something. :-\"

---

### Post by loboes41 on 2012-07-20
> **tulipán said:**
> my solution to the same problem (hp g62) is to lift the laptop and put it on a book, so it is still in a comfortable slopy position for typing and i'm giving the fan more air. i know this is NOT the kind of solution preferred here, but as long as i cant find a software/setting solution, i have to do something. :-\"

This is a firmware bug that is not actually related to the temperature of the laptop. Unfortunately, keeping it cooler does nothing to solve the issue.

---

### Post by tulipán on 2012-07-20
> **loboes41 said:**
> This is a firmware bug that is not actually related to the temperature of the laptop. Unfortunately, keeping it cooler does nothing to solve the issue.
Am so sorry for being such an ignoramus. i was just trying to help. Keeping it cooler does prevent shutdowns on my comp. sorry again.

---

### Post by josvanr on 2012-12-08
> **IDLCR said:**
> ok, sorry for taking so long to answer and maybe you all have already solved it, the problem disappeared when i updated the bios, the last one from HP support page and now the problem is gone, F.52

hello

I also have that problem. Updated to the latest bios F.1C but it is also present there ! The file F.52 is no longer available on hp's site. Do you have it lying around still? I'd like to get my hands on it!

much obliged,

josvanr

---

### Post by vjpanwar on 2013-03-06
HI sir 
  Did u get the solution of over heating,  please provide me the solution if you got.

regards
Vijay
[EMAIL="vijaypanwar.4u@gmail.com"]vijaypanwar.4u@gmail.com[/EMAIL]

> **IDLCR said:**
> Hello! this is my first thread in this forum since im using ubuntu (2009)usually all my questions or problems get resolved in here but latley im having one that i cant find a possible solution 

Recenlty i bought a notebook (HP Pavilion g4-1064)since day 1 i wanted to install ubuntu which i suceed to without any problems my problem start when i restart the notebook a "Thermal Shutdown Ocurred" alert is displayed before i can even load the OS but the computer NEVER shutdown while in use even on heavy load, i installed lm-Sensors and it says my core temps are 47c idle to 67c under heavy load, which i think are normal temps because even under Windows 7 the temps are almost the same ( +- 2c )btw i think its good to say that when im under windows and i restart the pc the thermal shutdown ocurred display doesnt happen which makes me think that is something with Ubuntu doesnt communicate with the bios or something i have istalled the latest drivers and BIOS from HP support page but the error its still displaying

in resume
the notebook displays a Thermal Shutdown Error even when my notbeook its cool and never shutdown while in use its only when i restart the PC FROM ubuntu, from windows its ok

Hope i get explain ( Spanish its my native so i have some trouble explaining in english ) i really wish someone could help me, tough the Error Display its just .... an error its annoying Thanks

Sorry i forgot
Specs

core i3 2310m
intel hd Graphics 3000
320 hitachi Hdd
3gb 1333mhz Ram

---

