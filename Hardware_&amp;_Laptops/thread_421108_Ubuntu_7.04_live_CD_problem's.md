---
title: "Ubuntu 7.04 live CD problem's"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by cubeshot on 2007-04-24
As the tittle says...  my problem starts at  hardware  checking were i get  4x error  on "bcm43xx_microcodes.fw"

my specs are : 

Nvidia GeForce Go 7200
HP pavilion dv 6000
PhoenixBios 4.0 release 6.1
AMD Turion 64 X2 Mobile Technology tl50 
512 mb drr RAM

currently running XP home

if you know any futher  problems  with ubuntu on  my laptop  specs plz do tell me :) 
i really like to try a diffrent OS for a change :)

---

### Post by Spr0k3t on 2007-04-24
Is this when the LiveCD boots or after the desktop is done loading?  The bcm43xx_microcodes.fw is related to the wireless card in the system.  Try disabling the onboard wireless and see how far you get.  If you can, from the terminal/console, post the response from "lspci" back here so we can get more information.

---

### Post by cubeshot on 2007-04-24
Well i just  boot from the CD  and go *start ubuntu and install* on the first menu ... after that  kernel starts  loading stuff and  does these diffrent test before i get to the live ubuntu desktop.. but i get that error when its testing  hardware.. i can turn off my wireless   off with a switch on my laptop  but  dunno if that cuts out  when my laptop start up with the live cd...

---

### Post by cubeshot on 2007-04-24
well  i turned off the wlan onboard my labtop... it stopped at  loading hardware .. nothing .. no error msg to give me any pin point of my problem... and cd-rom  eventually went still after 10 min

---

### Post by Spr0k3t on 2007-04-24
What you may have to do is try the alternate install CD.  I know this will not give you the live session so you can try before you install, but it's still an option.  One thing I can think of would be to check the MD5 checksum of the disc to see if that may be one of the problems.

---

### Post by cubeshot on 2007-04-24
alternate cd install ? hmm is there an alternate  cd install to ubuntu 7.04 ?

---

### Post by Spr0k3t on 2007-04-25
Yup, there is.  If you go over to the [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) you will see a checkbox at the bottom of the page which states: "Check here if you need the alternate desktop cd suited for computers with less than 256MB of RAM".  The alternate CD usually works better than the live disc.  So, if you are willing to install the distro on a spare portion of your drive, it would be an excellent place to start.

---

### Post by Jancuhl on 2007-05-04
hey,
also have the same problem.
Running a
 
HP pavilion dv 2000
Nvidia GeForce Go Graphics
PhoenixBios
AMD Turion 64 X2 tl50
1GB RAM

the installation CD (Live) I used worked perfectly on another system.


-->Cubeshot
 Did the alternate installer work for for you?

---

### Post by cubeshot on 2007-05-04
well i might try soon,, since im in the army i got limited spare time and well energy to think about it :P
think i'll try  in this week 

sorry the delay answear

---

### Post by cubeshot on 2007-05-08
okey so i installed ubuntu amd64 alternate on my lappy... i cant tell for certain whats the problem.. 
after  choosing the boot  and loading screen  stops randomly  .. even if its done loading it stops with black screen... heard that ubuntu got problems with wireless broadcom  and nvidia gfx  does this affect the startup of ubuntu ? ::confused:

---

### Post by biffta on 2007-05-08
> **cubeshot said:**
> okey so i installed ubuntu amd64 alternate on my lappy... i cant tell for certain whats the problem.. 
after  choosing the boot  and loading screen  stops randomly  .. even if its done loading it stops with black screen... heard that ubuntu got problems with wireless broadcom  and nvidia gfx  does this affect the startup of ubuntu ? ::confused:

If the screen's gone all black more than likely the X server has failed to load. Try booting again from the CD but this time before you choose "Start or install" press F4 and pick a low(ish) resolution. You could also try selecting "Start Ubuntu in safe graphics mode".

You may also find the following guide useful for other problems you may encounter with this laptop!

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

---

