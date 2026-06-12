---
title: "how come I can boot/install ubuntu 9.04 but not 9.10 (only with noapic)"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by xxxhsbxxx on 2009-11-12
Guys, I've been using Ubuntu for a year now (9.04) and last week I upgraded my distribution to 9.10. Ok, then I boot and it fails. No problem, waht I really wanted to do was a fresh install, but then when I tried to boot from the cd 9.10, I select install, and it hangs on with a cursor blink. I tried several solutions on the web and botting with noapic=off option worked. I installed, but then again every time I boot I need to turn off noapic.

My question is, why???

I can boot other ubuntu distros fine, debian, opensuse, whatever, but why do I need to turn off noapic in order to boot ubuntu 9.10???

How do I fix this?

any help is appreciated

tks

---

### Post by wojox on 2009-11-12
Couldn't tell you why, but I can make it stick 

```
gksudo gedit /etc/default/grub
```

Look for

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```  

and make it

```
GRUB_CMDLINE_LINUX_DEFAULT="noapic=off quiet splash"
```

Then:

```
sudo update-grub
```

---

### Post by xxxhsbxxx on 2009-11-15
Yeah I know I could do that so I don't need to turn off noapic every time, but what I really want is to use ubuntu 9.10 with noapic!... You all know the issues involved in using the OS with noapic off.

I just don't understand why this is happening, and why now with this distro??!!:shock:

I really want to upgrade into 9.10, but I think I'll have to stick to 9.04... this makes me sad ](*,) 

I also know a lot of people are getting the same issue, and no one seems to find a good solution (besides noapic and things like that)

Any good soul out there have an insight???

---

### Post by xxxhsbxxx on 2009-11-19
guess I'm all alone...

---

### Post by sam_sunders on 2009-12-14
> **xxxhsbxxx said:**
> guess I'm all alone...


no you're not...sigh...

---

### Post by Creak on 2009-12-25
Same here... I just tried to install the 9.10 on a Toshiba Satellite A110. Without any option, I've just got a blinking cursor. With noapic, nolapic I can boot some times, but most of the times it freezes.

Eventually, after few hours trying to bot on the 9.10, I tried with the 9.04 and it worked just fine!

But even if it is for a laptop or for a desktop, I think the 9.10 has a lot of regressions :(
I really hope the 10.04 will be more stable.

---

### Post by nyaggi on 2010-01-13
Estoy tratando de instalarlo probado MODO GRAFICO SEGURO y avanza hasta la pantalla de selección de idioma o hasta el particionado de disco y ahí se traba... ...crash...

22:51--Probando con noapic
22:56--Instalando... (Creo que es por pura suerte)
22:58--Comiendo algo rico mientras espero...
23:00--Instalación al 38%
23:10--Instalación al 64%
23:18--Instalación al 95%
23:22--Reiniciando sistema
23:23--Booteando... ...linea parpadeante... ...crash.

23:26--probando de nuevo... logo ubuntu... ...crash.

23:31--Booteando con noapic... logo ubuntu... ...carga ubuntu... ...crash
23:31--Reintentando... logo ubuntu, carga ubuntu, FUNCIONA!!!

:popcorn:

23:34-- CRASH!!!   :(
Otras opciones para probar
nolapic
noapictimer

23:43-- Funcionando!!! usé las opciones noapic noapictimer editando el grub

---

### Post by axelsvag on 2010-01-27
I can confirm this bug on my Toshiba aswell. Have you filed a bug report?

---

### Post by ashokgm on 2010-01-27
[http://linux-solution-for-us.blogspot.com/](http://linux-solution-for-us.blogspot.com/)

---

### Post by ub_beginner on 2010-02-08
Hello
I have the same problem with a desktop
As a complete beginner - I have no idea how to boot with "noapic". 
1             How do I interupt the booot sequence

---

### Post by ub_beginner on 2010-02-08
> **ub_beginner said:**
> Hello
I have the same problem with a desktop
I have downloaded the latest version - 9.10
As a complete beginner - I have no idea how to boot with "noapic". 
1 How do I interupt the booot sequence
2 How do I the add the "noapic" parameter  and to what.
 
Sorry this is even pre- beginner but the help says use the noapic option but does not tell how to do it. 
 
 
Would I be better downloading an earlier version?
RGDS

---

### Post by axelsvag on 2010-02-09
In start of the boot sequence with the live disk you get a menu at the bottom. If you choose F6 you can choose among other suggestions " noapic "

---

