---
title: "First time user to Ubuntu, have installation problem."
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by out-of-hand on 2009-04-10
hi guys... 

been a Microsoft user all my life ... came across Ubuntu ... EXCELLENT !!!! i love it.

i have made a live cd. and installed Wubi- through windows ...
i have a problem, not sure what to do .... please can anyone help?


i have 2 HDD

i have 1 hdd thats 20GB that holds my XP installation 
i have a 2nd Hdd  500GB - i dedicated to moves and Ubuntu installation.


after the installation ... all appears fine . 
once i reboot ... i get 2 options .

XP PRO start up 
Ubuntu

so i select ubuntu to load up ...
its stops me by Grub> 

now im confused ? am i missing something ?

however if i boot up with the live CD in my box... it offers me options to boot up or install .

and i chose to start up without installing on hdd option ... and its starts like a dream ....

but i cant seem to get past the GRUB> on my pc boot options .

i have tried uninstalling it ... perfectly done . when i re install it ... via boot up mode via live CD ... after all's done .. i stil get that Grub> ....


anything im missing ? can any one assist me on this ?


Many thanks in Advanced 

Out-of-Hand

---

### Post by Cerberus108 on 2009-04-10
Hi there, I hope I will be helpful. First of all, if you have two distinct HDD, the best option is to install ubuntu from the live cd: it's quite simple, you have to load the cd at boot-time, and after it's loaded, double-click on the "install" icon on the desktop.

(Obviously, be sure to make a backup of all of your important data, better if on a dvd or a usb stick)

After that, you just have to follow the installation steps: in case you need help, you will find plenty of tutorials and guides on the net, you have just to google it, you could be able to do it from the very live cd, just click on the firefox icon on the panel. Let us know if you had some luck with it..

---

### Post by out-of-hand on 2009-04-10
> **Cerberus108 said:**
> Hi there, I hope I will be helpful. First of all, if you have two distinct HDD, the best option is to install ubuntu from the live cd: it's quite simple, you have to load the cd at boot-time, and after it's loaded, double-click on the "install" icon on the desktop.

(Obviously, be sure to make a backup of all of your important data, better if on a dvd or a usb stick)

After that, you just have to follow the installation steps: in case you need help, you will find plenty of tutorials and guides on the net, you have just to google it, you could be able to do it from the very live cd, just click on the firefox icon on the panel. Let us know if you had some luck with it..




hi there, thank you for your reply ...
i have seen that i can use the live Cd to brows internet , excellent stuff..

i have also installed ubuntu from desktop of XP. get me to Grub> with menu's 

i chose the second harddrive which is a SATA. and it allows me to install it ...
i have been looking on the net as to why i get stopped at GRUB> and cant (dont know how to) boot into ubuntu
.

any other suggestions ? 
thank you once again .

---

### Post by Cerberus108 on 2009-04-10
You're welcome :) 

It would be a nice thing if you upload here a screenshot (maybe even shot with a cellphone) to let me figure out better what the problem is. 

If you are unable to do it, can you post here a thorough description of the screen where you get stuck, please? Thank you :)

---

### Post by out-of-hand on 2009-04-10
> **Cerberus108 said:**
> You're welcome :) 

It would be a nice thing if you upload here a screenshot (maybe even shot with a cellphone) to let me figure out better what the problem is. 

If you are unable to do it, can you post here a thorough description of the screen where you get stuck, please? Thank you :)

here is the attached picture ... 
ill explain it again . 

i have 2 HDD.  one is 20 GB IDE - win xp

other one is 500Gb Sata 


i have installed Ubuntu through windows choosing the 500GB , installs perfect.
once i reboot ..

i get the option to boot into XP or Ubuntu.
if i choose Ubuntu...
i get stopped at Grub>


suggestions ?

---

### Post by Cerberus108 on 2009-04-10
I have seen your screenshot, it is a strange situation, I can't figure out why it doesn't boot into ubuntu. I'll try to explain in the best way another method to install ubuntu:

You have installed ubuntu in a way where it depends on windows to load properly: this happens when you install it through wubi. It surely is simple to install this way, but sometimes you could experience problems. 

The other way to install ubuntu, which is in fact the standard way, is to write the ISO image of ubuntu on a disk, put this disk in your computer, and reboot it. 
The disk should have loaded a screen where you will be prompted to decide what to do, whether to install ubuntu, or to try it, et cetera. You said you already got there, excellent. Now, you should start ubuntu from the live cd, and from there, NOT from windows, start the install process. I know, it's a little harder to do it, expecially for a beginner: if you have any question about any install step, try post them here. :)

---

### Post by out-of-hand on 2009-04-10
ok ... thanks... let me go back and try again ... ill remove it completely (ubuntu) and install if when i boot up with the live cd...

let me try it this way ... 
thanks again for your help ...
will come back if problem persists

Out-of-Hand

---

### Post by Cerberus108 on 2009-04-10
You're welcome, I hope it will work fine :)

P.S. Don't forget to mark this thread as "SOLVED" once you make sure you have not problems anymore.

---

### Post by wildman4god on 2009-04-10
the problem is the install from inside windows option is meant to install Ubuntu on the same partition as windows on a virtual hard drive, if you have a second hard drive just install directly to that using the live cd, you'll get better proformance than the install inside windows option (called wubi).

---

### Post by out-of-hand on 2009-04-14
> **wildman4god said:**
> the problem is the install from inside windows option is meant to install Ubuntu on the same partition as windows on a virtual hard drive, if you have a second hard drive just install directly to that using the live cd, you'll get better proformance than the install inside windows option (called wubi).

:) many many thank you's :)
i actually did what you suggested before i read ur post today..

i formatted my 40Gb Hdd and installed ubuntu by restarting into the live cd... choosing install ubuntu... and formatted the partition again ... rebooted ... and could not see my 40Gb anymore ... but then i re formatted it to NTFS. and i used the ubuntu live cd through windows ... installed it via windows . and im Happy its working 100%....

thank you all for your Excellent help ! ") im loving this alot ...


i tried to get the 3d Desktop ... browsing Google and cant find the best way to install 3d desktop ....


anyways thank you all once again :)


where do i find marking this thread as solved ?

---

