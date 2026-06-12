---
title: "Nvidia drivers botch"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Renigade on 2009-03-11
I am completely new to Ubuntu so for starters I will give my system and install order. Seeing as I have no idea what information is needed to help me.

System:> AMD Phenom 9850 on Gigabyte 790X DS4 8 giga of PC8500 1066@800 Asus 8600GT silent 500GB SATA Master 80GB IDE slave
Instalation order
1) XP Pro X64 on 500GB SATA 
2) 80GB IDE added 
3) installed Ubuntu 8.10 on the 80GB IDE HDD. 

A friend told me that 8.04.2 is better for Folding(the reason for Dual booting Ubuntu)
So I then installed 8.04.2 over the 8.10 (reformated)
 
I installed updates no problem followed this guide to install the FAH6 SMP client [http://forums.overclockersclub.com/index.php?showtopic=160706](http://forums.overclockersclub.com/index.php?showtopic=160706) with no problems

I installed WINE next with no problems from this guide [http://wiki.winehq.org/HowTo](http://wiki.winehq.org/HowTo)

Then wile trying to install the NVidia drivers from this guide here
[http://foldingforum.org/viewtopic.php?f=52&t=6793](http://foldingforum.org/viewtopic.php?f=52&t=6793)
[COLOR="Red"]**at step 8 I got an Error **[/COLOR]
```
          NVIDIA Accelerated Graphics Driver for Linux-x86_64 (180.29)




 
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.

                                       OK  










  NVIDIA Software Installer for Unix/Linux                      www.nvidia.com 
```

I appologize if there is an answer to this question elsewhere in the forums that I had not found. I wanted to make sure of a solution for my particular Noobishness before blundering blindly with solutions I am not 100% sure fit my situation/scenario.

Thanks in advance
Renigade The Ubuntu n00b

---

### Post by Neo_The_User on 2009-03-11
open up a terminal

```

sudo /etc/init.d/gdm stop

```

Try running the install again from command line. You'll need xorg-dev.

```

sudo apt-get install xorg-dev dh-make build-essential debconf debhelper

```

---

