---
title: "CPU fan does'nt work ( thinkpad l512)"
date: 2010-07-19
forum: Hardware
---

### Post by nes125 on 2010-07-19
Hello everyone
 
i just got a new lenovo thinkpad L512 with a core i5 m430.
the problem is that i've run into is that when i start my ubuntu 10.04 the fan stops spinning al together.
 
does anyone have a idea how to fix this because i don't want to go back to windows :(

---

### Post by PresenceofMind on 2010-07-19
> **nes125 said:**
> Hello everyone
 
i just got a new lenovo thinkpad L512 with a core i5 m430.
the problem is that i've run into is that when i start my ubuntu 10.04 the fan stops spinning al together.
 
does anyone have a idea how to fix this because i don't want to go back to windows :(

Hello :D

Please don't go to Windows.........yet......

Here, try this code and see if you get some response. This will test your fans and see if it has any problems controlling fan voltage:

```
sudo pwmconfig
```Hope this sheds some light!!!

---

### Post by nes125 on 2010-07-19
Thanks for the quike respons.

i tryed the command you gave me but it seems there are no sensors on my motherbord that use the programe
i lookt throuh the internet some more. the next thing i found out 
```
-laptop:/proc/acpi/thermal_zone/TZ00$ cat cooling_mode 
0 - Active; 1 - Passive
 

```

---

### Post by PresenceofMind on 2010-07-21
> **nes125 said:**
> Thanks for the quike respons.

i tryed the command you gave me but it seems there are no sensors on my motherbord that use the programe
i lookt throuh the internet some more. the next thing i found out 
```
-laptop:/proc/acpi/thermal_zone/TZ00$ cat cooling_mode 
0 - Active; 1 - Passive
 

```

Ah, I see...... so you have passive cooling? That means it doesn't use a fan...

---

### Post by nes125 on 2010-07-21
no it has a active cooling it just means that i't turns my fan off and the real issue nou is how do i turn it on

---

### Post by PresenceofMind on 2010-07-21
> **nes125 said:**
> no it has a active cooling it just means that i't turns my fan off and the real issue nou is how do i turn it on

that's weird......i tried the same command on my system and it also said passive. But I know it hasn't turned my fan off... cos i can see that it's still running. Can a kernel update solve all this?

---

### Post by nes125 on 2010-07-29
sorry for the late reply. 

uhm yeah i tried that to O.o i just did som reading in the thinkpad_apci ( it's a driver set or something that is made for thinkpads and aparently they havend included my thinpad O.o so i think i'l need to waith for a update. O.o 

if anyone has another idea id love to hear it ^^ and much thank PresenceofMind

---

### Post by kleskjr on 2010-07-29
you could try asking at [http://forums.lenovo.com/](http://forums.lenovo.com/)

there is a linux section..though they didnt answer my question there, wish you will have more luck

---

### Post by joost1123 on 2010-08-16
Has this problem been solved?

---

### Post by tadaskr on 2010-08-17
I have same problem with my toshiba laptop. My fans don't start on cold start too and linux don't want turn on fans until CPU reaches 84C. So, When I start pc on cold start I wait on boot menu until pc warm up and fans start spinning :)

---

