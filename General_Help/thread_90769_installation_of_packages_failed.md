---
title: "installation of packages failed"
date: 2005-11-15
forum: General Help
---

### Post by ralph4100 on 2005-11-15
I'm installing ubuntu on a PC also running Windows XP, and during installation, the installation of the packages failed, because either I had run out of disk space or the cd reader was having trouble. It must have been the cd reader, or perhaps the cd, because I know I had plenty of space to install (70GB).

I proceeded with installation anyway, and then restarted my computer. Now the installation process is "Installing Packages: Preparing for installation..." but it is stuck on 0%. What should I do?

---

### Post by kruz on 2005-11-15
this is why i love live cd's
actually boot back in, erase the partition and start install over again

---

### Post by ralph4100 on 2005-11-15
how do I boot back in and erase the partition?

...sorry...

---

### Post by kruz on 2005-11-15
put your ubuntu CD back in your drive
make sure if its USB you have boot usb in dos


this wuz my problem
make sure the cd is clean
and the burner/drive is not hot and u just didnt use it a bunch

restart, boot into ubuntu with teh option boot: hit the options menu i think f1 and f2? or something there is a dMA control i cant remember it, ill check for it later, but it mighta just got hot, so boot again, go to the partition manager, i think its number 3 then delete everything accept ur windows partition, and let ubuntu setup ur hd for u

---

### Post by ralph4100 on 2005-11-15
ok I followed your steps and, per option 3, booted with the "memtest" option, which is hopefully what will allow me to delete the linux partition and reinstall...

---

### Post by kruz on 2005-11-15
dont know why u memtested
but if you find the whole thing about partition tables

its a pretty easy menu like 1-9 i believe just select partion something

im not sure exactly it wuz awhile ago i installed ubuntu

get back with me on ur progress

---

### Post by ralph4100 on 2005-11-15
The F1 option page includes these options
1-the help page index
2-prerequisites for installing Ubuntu
3-boot methods for special ways of using this cd-rom
4-special boot parameters, overview
5-special boot parameters for special machines
6-special boot parameters for selected disk controllers
7-special boot parameters for the install system
8-how to get help
9-about
10-copyrights

option 3 includes 4 available boot methods

linux (default)
expert (maximum control)
server, server-expert (for servers)
memtest (memory test)

I thought that since I was trying to reformat the partition (memory) that memtest might be my option. 

obviously it wasnt......

thanks for your help, btw. hopefully you're still online....

---

### Post by kruz on 2005-11-15
lol yes ill be here for acouple more hours

and no memtest=ram im pretty sure

boot with the command linux

and wait for everything ot load and u will have a blue menu screen
try to find the option for partitioning

or maybe just start with a clean install
either way at the boot line use the command 

linux

---

### Post by ralph4100 on 2005-11-15
well before I saw your above message I had booted with expert... so I tried to use the partitioning menu to reformat the partition in question. There are more options on expert and it kept failing to work.

I'll boot with linux an see how that goes...

---

### Post by kruz on 2005-11-15
im pretty sure that expert wants u to set ur cylinders automatically on where u wana partition
and frankly having ubuntu setting it up
by itself is alot easier, as it takes ur pagefile and half ur ram
lol pagefile, sry, swap partition personally i add 256 then divided so my swap is 512 megs andi have 768 megs of ram
runs nicely if u dont mine loosing a lil space big deal

---

### Post by kruz on 2005-11-15
i ahve to go ill be back in approx 15 hours or so

keep working at it, taht should be all the info u need
since u havent been back i hope its working
gl!

---

