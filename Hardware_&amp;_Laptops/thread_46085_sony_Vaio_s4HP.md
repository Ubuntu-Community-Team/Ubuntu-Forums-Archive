---
title: "sony Vaio s4HP"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by 89c51 on 2005-07-03
first i want to say hello to the whole ubuntu community

i purchased a sony vaio s4hp and decided to install Ubuntu hoary on it

in the begining the boot hanged but i managed to overcome this by using acpi=off parameter

everything else went great (it recognized the 1200x800 resolution automaticaly)

i managed to configure the sound by instaling the latest alsa driver (+lib, +oss, +utils) from the alsa project (instructions [here](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto) 

the problems now are:

1) i cant make the cpu frequency monitor and battery monitor to work
(they appear on the panel but neither of them works)

2)also sometimes when i boot in the login screen and later in grome the colos of the screen are faded and i have to restart the computer

3)also when the kernel boots i get awarning about PnPBIOS and a temporary failure in name resolution  [fail]
can any of those cause truble

4)when the computer is pluged in the fan works constantly and when on battery it  doesnt seem to work

5) also i tried to install sonypi (for the Fn keys) but didnt work (caused errors)


any solution to the above would be very helpfull


this is the first time i try installing/trying linux on any machine (except live cds) and i'm a noob

---

### Post by 89c51 on 2005-07-05
the screen problem is solved

i installed the 7667 nvidia driver

---

### Post by ranf on 2005-07-05
[QUOTE=89c51]
5) also i tried to install sonypi (for the Fn keys) but didnt work (caused errors)
[/QUOTE]

"caused errors" is not really helpful. **What** errors do you get?

---

### Post by 89c51 on 2005-07-05
ranf

i tried again and the instalation went fine (sonypi and spicctrl) but still the fn keys dont work (screen brightness,volume control etc)

---

### Post by ranf on 2005-07-05
[QUOTE=89c51]
but still the fn keys dont work (screen brightness,volume control etc)[/QUOTE]

I have a Sony C1VE. With the program "rsjog" I can use the Fn-keys and then the jogdial.

---

### Post by 89c51 on 2005-07-05
thanks i ll try it tomorow and anounce the results

---

### Post by 89c51 on 2005-07-10
not working:

1) acpi

tried grub with acpi=on and acpi=forced but the sytem hanged

2)Fn keys tried sony_acpi but with no acpi (see above) ...

3)and probably the memory stick slot


to be tested:

firewire
wireless 
bluetooth
pcmcia

those seem to be detected by ubuntu

---

### Post by mquade on 2005-07-24
Hi, I'm currently writing on an How-To concerning the S4HP.
I started today to write it, so it's not very well done and no realy amazing informations. But I'll keep it up to date and in a few days it will be a good help for everybody whith this stylish new NB.
Try this link: [VGN-S4HP How-To](http://matthias-qua.de/linux/laptop/sony_vaio_vgn-s4hp/) 
Maybee it will help you solving some probs.
Feel free to send mail to mail(at)matthias(minus)qua(dot)de

regards, 
matthias

---

### Post by 89c51 on 2005-07-25
matthias thanks 

i also found this link (on [gentoo forums](http://forums.gentoo.org/viewtopic-t-361872.html) ) for controling  screen brightness

[http://www.acc.umu.se/~erikw/program/smartdimmer-0.1.tar.bz2](http://www.acc.umu.se/~erikw/program/smartdimmer-0.1.tar.bz2)

download 

./config
make

and write smartdimmer  (ender) on the command line

it has 21 levels of brightness

nice stuff :)  :) 

i m having problems installing 2.6.12.3

i'll try with your .config

as for the memory problem on your laptop
i contacted kingston on how i can get 2gb of ram and they told me the motherboard supports only 1gb
i dont know if we can hack the motherboard or even if this info is true because the spec sheet clearly states that the memory can be expanded to 2gb

on the sony site the specs are for 1gb max

i have contradicted info on this one

---

### Post by ninja_indiano on 2005-07-27
[QUOTE=89c51]

in the begining the boot hanged but i managed to overcome this by using acpi=off parameter
[/QUOTE]

When I try to install Ubunto it freezes at 98% when it is detecting hardware....most specific at de acpi parte....

How do I put acpi=off? 

Thanks

---

### Post by 89c51 on 2005-07-27
[QUOTE=ninja_indiano]When I try to install Ubunto it freezes at 98% when it is detecting hardware....most specific at de acpi parte....

How do I put acpi=off? 

Thanks[/QUOTE]

i dont remember exactly how i did it but it was during the instalation

when you install ubuntu you can use additional instalation commands

look in the help during the instalation

---

### Post by 89c51 on 2005-07-31
i tried to install a new kernel (2.6.12.3)

i downloaded the new kernel
and (on the directory i untared)

make config
make bzImage
make modules
make modules_install
make install

when i give the mkinitrd commant (in the boot directory) i get the following

usr/sbin/mkinitrd: add_modules_dep_2_5: modprobe failed
FATAL:module ata_piix not found
FATAL:module sd_mod not found
Warning: this failure may indicate that your kernel will not boot but it can also be trigered by needed modules being compiled into the kernel
cpio (0xfffe000) :no such file or directory
cpio /lib/ld-linux.so.2 (0xbdfeb000) :no such file or directory
find /lib/modules/2.6.12.3/kernel/drivers/acpi :no such file or directory

i tried mquades config and others with similar results
any help would be welcome

---

### Post by 89c51 on 2005-08-10
[COLOR=Red]UPDATE[/COLOR]

after getting a broadband connection and managing to mess the system so bad that i couldnt save it with recovery mode i decided to install ubuntu 5.04 again

this time i used the parameter expert and nothing else

this time i used reiserfs

everything went fine -acpi is working- and all the devices where recognized automaticaly
 me some trouble
after the instalation finished i updated the packages eith apt get (following ubuntuguide.org)

the only thing that wasnt working was the sound but it solved after i instaled the latest alsa 
**install alsa last -it gave me trouble (sound wasnt working) after i updated some packages

---

### Post by NikoC on 2005-11-07
So you now are running ubuntu 5.04 on a Sony Vaio s4hp with everything working (sounds, hybernate, ACPI, graphics, ...)? Perhaps i should try the 5.04 also, i have the same laptop but Breezy still has some flaws (like the hybernate function)...

---

