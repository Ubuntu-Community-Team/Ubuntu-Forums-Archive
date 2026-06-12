---
title: "amd 64 install problem"
date: 2008-08-13
forum: General Help
---

### Post by wajdislama on 2008-08-13
Greetings,

i want to install ubuntu 8 on my laptop:
* HP pavillon dv5000 
* AMD turion 64
*ATI radeon express 200M

***)the installation process stop at the begining with just a black screen

***) i tried several ubuntu distributions and i checked the installation CDs without any error

***) i tried the "noapic" option and then after loading the kernel  i get message like " daemon start failed" and then ... black screen

***) i ve seen a lot of conflicting posts everywhere about this, some solutions have worked for others but none for me

I really need any help, any idea, any suggestion about my problem
i am really stuck....
plzzzzzzzzzzz HELP ME ! ! ! ! !  :(

---

### Post by wajdislama on 2008-08-13
Greetings,

i want to install ubuntu 8 on my laptop:
* HP pavillon dv5000 
* AMD turion 64
*ATI radeon express 200M

***)the installation process stop at the begining with just a black screen

***) i tried several ubuntu distributions and i checked the installation CDs without any error

***) i tried the "noapic" option and then after loading the kernel  i get message like " daemon start failed" and then ... black screen

***) i ve seen a lot of conflicting posts everywhere about this, some solutions have worked for others but none for me

I really need any help, any idea, any suggestion about my problem
i am really stuck....
plzzzzzzzzzzz HELP ME ! ! ! ! !  :(

---

### Post by overdrank on 2008-08-13
Hi and welcome, please do not create multiple threads on the same issue. :)

---

### Post by overdrank on 2008-08-13
> **wajdislama said:**
> Greetings,

i want to install ubuntu 8 on my laptop:
* HP pavillon dv5000 
* AMD turion 64
*ATI radeon express 200M

***)the installation process stop at the begining with just a black screen

***) i tried several ubuntu distributions and i checked the installation CDs without any error

***) i tried the "noapic" option and then after loading the kernel  i get message like " daemon start failed" and then ... black screen

***) i ve seen a lot of conflicting posts everywhere about this, some solutions have worked for others but none for me

I really need any help, any idea, any suggestion about my problem
i am really stuck....
plzzzzzzzzzzz HELP ME ! ! ! ! !  :(

HI and welcome, have you tried the alternate cd, it is for installation as it is text based? Also have you tried using the F4 option booting the live cd, there you can change the resolution.

---

### Post by taseedorf on 2008-08-13
Hey man, try removing the "splash" from kernel loading at boot...

when asked which to select before you install....click custom...and remove "splash" and remove "quiet"......

that should work. almost positive. thank me later ;)

if not (which it should)
download the alternate installer...which worked for me when others didnt.....

---

### Post by wajdislama on 2008-08-13
ok,,
***)at the begining, i get this boot option:
[COLOR="DarkRed"]file=/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz quiet --[/COLOR]
i didnt find the "splash" thing

when i removed "quiet" it worked a litle and then same thing

when hiting F4 i only get one item "normal"
i guess i should try the alternate installer

thanks anyway ;)

---

