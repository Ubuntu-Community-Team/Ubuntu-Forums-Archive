---
title: "Problem with Hibernate"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by solx on 2006-05-04
Hi, 
Im using a Compaq Presario 1700T. If I choose System->Logout->Hibernate, the computer will breifly go into Hibernate mode, but after about 1 second it will wake up again. This happens consistently and without any action from keyboard or mouse.

Any suggestions?

---

### Post by Efrain Valles on 2006-05-04
[QUOTE=solx]Hi, 
Im using a Compaq Presario 1700T. If I choose System->Logout->Hibernate, the computer will breifly go into Hibernate mode, but after about 1 second it will wake up again. This happens consistently and without any action from keyboard or mouse.

Any suggestions?[/QUOTE]


I have the same exact laptop and mine won`t come back from hibernation... :( I get a black screen and no way of bringing it back... any suggestions...

off topic

does yours come with the same Ati card??? (radeon mobile MY L7 ????)
if so did you get it working with 3d accel... I want to add the composite.... but I can`t until I get 3d acc... :(

---

### Post by snipe122 on 2006-05-06
does it really write the hibernation things or does the screen only turn black? does the comp turn off when you hibernate? does grub appear when you turn the comp on again? what happens then? the ubuntu start-screen?

did you set the resume-option in your menu.lst? how many memory do you have and how big is your swap-partition?


greetz
snipe

---

### Post by solx on 2006-05-06
It does some writing to disk, I dont know how to tell if it is writing the hibernation stuff. It appears to powerdown, at least the harddrive spins down. I dont see grub, then it asks for password.

I dont see anything about resume in menu.lst.

I dont know how to figure out how much RAM or swap I have, but that might pertain to the problem, because I know that I dont have much swap, something like 37megs.

---

### Post by snipe122 on 2006-05-06
hmm ;)

you should check it out how much swap you have... you can do it with gparted for example (just install with synaptic) and you should know how much RAM your pc has...

greetz
snipe

---

### Post by Efrain Valles on 2006-05-07
[QUOTE=snipe122]does it really write the hibernation things or does the screen only turn black?[/QUOTE] It writes then the screen turns black


 > does the comp turn off when you hibernate? 
not it doesn't it only goes blanc, I can still hear the hardrive and the power light is on. 
> does grub appear when you turn the comp on again?
always, but since I have to shut down manually, It checks my partition because it wasn't unmounted properlly

>  what happens then? the ubuntu start-screen?
Eventually 
YEs... a fresh boot I call it 



d> id you set the resume-option in your menu.lst? how many memory do you have and how big is your swap-partition?
WHAT RESUME Option... Where ????, memory I have 256 RAM and I made a Swap file of 500 megs

CHEERSSss

---

### Post by snipe122 on 2006-05-07
okay... it strange that it writes... but maybe its not that...

edit your /boot/grub/menu.lst

edit the line # kopt=root=/dev/hda2 ro (hda2 is my ubuntu-boot-partition, change if necessary)

to

# kopt=root=/dev/hda2 ro resume=/dev/hda5 nolapic noapic (hda5 is my swap-partition, change it to yours)


now good luck!

---

### Post by Brent Dax on 2006-05-08
[QUOTE=snipe122]
# kopt=root=/dev/hda2 ro resume=/dev/hda5 nolapic noapic (hda5 is my swap-partition, change it to yours)
[/QUOTE]
I had the same problem, and this fixed it for me.  Thanks!

---

### Post by Efrain Valles on 2006-05-09
[QUOTE=Brent Dax]I had the same problem, and this fixed it for me.  Thanks![/QUOTE]

I don't have a sawp partition... I have a swap file.. :S

that's an Issue, isn't it?

---

### Post by snipe122 on 2006-05-09
Under Linux its nearly impossible to have a SWAP-FILE! SWAP is a filesystem, on an own partition, if you dont have its not possible to hibernate in the standard way. You need a swap-partition, if you dont have make one with partition magic or sth. else.

greetz
snipe

---

### Post by Efrain Valles on 2006-05-09
[QUOTE=snipe122]Under Linux its nearly impossible to have a SWAP-FILE! SWAP is a filesystem, on an own partition, if you dont have its not possible to hibernate in the standard way. You need a swap-partition, if you dont have make one with partition magic or sth. else.

greetz
snipe[/QUOTE]


Thanx...

---

### Post by flupdiflup on 2006-05-11
actually, you can easily have a swap-file. However, it isn't a very good idea :-)

---

### Post by will_in_wi on 2006-05-14
Using a Swap _File_ can be helpful in situations where you have one partition to fit everything in. FYI: To make a swapfile you use dd to create a file of the size you want, mkswap the file, then swapon the file. You can even put the file in fstab as a normal swap file.

---

### Post by snipe122 on 2006-05-15
of course you can have a swap file, but usually you have a partition... dont know if swap file works with hibernate cause it says it needs a partition... anyone who can try this with swap file?

---

