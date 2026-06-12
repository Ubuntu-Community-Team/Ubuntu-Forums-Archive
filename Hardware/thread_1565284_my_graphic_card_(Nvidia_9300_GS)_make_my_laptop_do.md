---
title: "my graphic card (Nvidia 9300 GS) make my laptop down after install!!"
date: 2010-08-31
forum: Hardware
---

### Post by mahan66 on 2010-08-31
Hi everybody,
I have a problem with my graphic card in ubuntu 10.04.
after ubuntu 10.04 installed, upgrade hardware warn me that 2 updates of my graphic card is avilable. 

my graphic card : Geforce 9300 GS
my laptop : vaio Z570N

when I get this 2 update and activate them, i restart the computer. when  it starts, everything I see is a black screen, and I had to turn off  laptop fysically!!

I install Ubuntu 4 times and this problem continued. this resolution  make my eyes bored. also without this graphic updates I cant use compiz  utilities.

could any one help me?
WRG

---

### Post by eGelor on 2010-08-31
> 
mahan66 I see is a black screen, and I had to turn off laptop fysically!!
I got this problem 3 months now. I'm not the expert but there are several thing that you can do and solve your problem.


first tell as if you can boot to X mode.
if yes go to your xorg file.
Quote:
> sudo nano /etc/X11/xorg.conf
Change driver to "nv" and reboot. you'll fix reso but no compiz.

if you got nvdia drivers load up and your xorg with nvidia driver load. go to you grub conf.
Quote:
> sudo nano /etc/default/grub
and change that line to
Quote:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
don't forget to update your grub by
Quote:
> sudo update-grub2
if you are luck enough maybe your problem will fixed up.

---

