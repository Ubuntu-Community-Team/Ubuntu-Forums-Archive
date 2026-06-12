---
title: "Cd Recording!!!"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by razor_88 on 2005-04-08
Hi, I just started using Ubuntu linux and can't burn any cd's I've tried using the cd writer built into gnome and gnomebaker but both lock up my computer.  ](*,)

What can I do to fix this. 

Thanks, Razor

---

### Post by n2024 on 2005-04-08
I never try gnomebaker but for me nautilus-cd-burner just sucks!

Try k3b, it's a kde based burner prog but the best i ever seen

Good luck

---

### Post by razor_88 on 2005-04-08
[QUOTE=n2024]I never try gnomebaker but for me nautilus-cd-burner just sucks!

Try k3b, it's a kde based burner prog but the best i ever seen

Good luck[/QUOTE]

I just installed k3b but still have the same problem, except this time I got this message, hdc: not ready for command 

 :-?

---

### Post by rocket.nz on 2005-04-11
[QUOTE=razor_88]I just installed k3b but still have the same problem, except this time I got this message, hdc: not ready for command 

 :-?[/QUOTE]
 i have the same problem its really slow and bring smy work station to a grinding halt. cpu usage 100%

---

### Post by rubinstein on 2005-04-11
Maybe you want to turn dma on for the cd drive if it is off.
hdparm /dev/hdc 
gives information about the current mode and
sudo hdparm -d1 /dev/hdc
turns dma on (if your drive is hdc)
CD-burning only works for me when dma mode is on.

Good luck
rubinstein

---

### Post by rocket.nz on 2005-04-11
[QUOTE=rubinstein]Maybe you want to turn dma on for the cd drive if it is off.
hdparm /dev/hdc 
gives information about the current mode and
sudo hdparm -d1 /dev/hdc
turns dma on (if your drive is hdc)
CD-burning only works for me when dma mode is on.

Good luck
rubinstein[/QUOTE]

cheers will try this tonight and let you know how it goes.

---

### Post by rocket.nz on 2005-04-12
awesome works a dream thx for the tip!!!

---

### Post by rubinstein on 2005-04-12
Good to hear that it works!

To make it permanent (maybe you did it already):
sudo gedit /etc/hdparm.conf

add the following to the end of the file:
command_line {
hdparm -d1 /dev/hdc
}

---

