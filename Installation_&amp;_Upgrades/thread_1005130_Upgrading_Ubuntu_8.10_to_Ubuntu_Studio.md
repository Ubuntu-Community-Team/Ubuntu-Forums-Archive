---
title: "Upgrading Ubuntu 8.10 to Ubuntu Studio?"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by someguy876 on 2008-12-07
I already have the normal Ubuntu 8.10 installed, but I want to upgrade to Ubuntu Studio 8.10. I know there was a way to do it in Feisty,  but what about in 8.10? Oh and I'm a VERY new linux user so don't go too technical on me :p

---

### Post by Partyboi2 on 2008-12-07
Open a terminal (Applications>Accessories>Terminal) and type in[FONT=monospace]
[/FONT]```
sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

---

### Post by Zeta_113 on 2008-12-13
Ubuntu Studio uses a modified kernel if I remember correctly; does this upgrade from Ubuntu to Ubuntu Studio also change the kernel?
If it does not, is there a way to do this?

---

### Post by logos34 on 2008-12-13
> **Zeta_113 said:**
> Ubuntu Studio uses a modified kernel if I remember correctly; does this upgrade from Ubuntu to Ubuntu Studio also change the kernel?
If it does not, is there a way to do this?

you'll need to add 

linux-rt

to partyboi2's command if you also want the real-time/low-latency kernel.

See this:

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)

---

### Post by SchindlerShadow on 2009-01-31
> **logos34 said:**
> you'll need to add 

linux-rt

to partyboi2's command if you also want the real-time/low-latency kernel.

See this:

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)

sudo apt-get install inux-rt
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package inux-rt

?????

---

### Post by Partyboi2 on 2009-01-31
> **SchindlerShadow said:**
> sudo apt-get install inux-rt
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package inux-rt

?????
Looks like you forgot the l in linux
```
sudo apt-get install linux-rt 
```

---

### Post by Kobayashi-kun on 2009-02-01
> **someguy876 said:**
> I already have the normal Ubuntu 8.10 installed, but I want to upgrade to Ubuntu Studio 8.10. I know there was a way to do it in Feisty,  but what about in 8.10? Oh and I'm a VERY new linux user so don't go too technical on me :p

I do NOT advise doing this. I tried out Studio and it gave a load of trouble with a "DPKG Error". If you want real advice, stick to Ubuntu or Xu and Ku.

---

### Post by SchindlerShadow on 2009-02-03
> **Partyboi2 said:**
> Looks like you forgot the l in linux
```
sudo apt-get install linux-rt 
```

thx XD

---

