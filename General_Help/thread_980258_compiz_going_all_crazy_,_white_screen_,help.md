---
title: "compiz going all crazy , white screen ,help"
date: 2008-11-12
forum: General Help
---

### Post by Rgrmartins on 2008-11-12
well before this, hi people 1st post.

not really used to linux, i'm using it to program some apps for school, but i'm thinking on making it my choice instead of windows, so i tried to put some fancy stuff, well went WRONG, really really wrong.

i started to install my graphic drivers,(ATI mobility radeon hd 2400) it was a pain in the *** (i think something went wrong there) after that i instaled compiz fusion the simple_ccsm and the other app to run compiz, and checked the blacklisting thing.

rebooted, after that i couldt start the OS, after the boot screen of ubunto appeared it would turn all black and stucked there, i had to use recovery tool, 
tryed to run compiz, result: crazy white screen, couldnt use anything.



oh and desktp effects still dont work
and my screen its all grainny:S 

well pls help me, i searched and i couldt find a solution :(

---

### Post by Izek on 2008-11-12
Which driver did you use? fglrx? Or the radeonhd?

---

### Post by Rgrmartins on 2008-11-12
> **Izek said:**
> Which driver did you use? fglrx? Or the radeonhd?

well i used the one for my graphics card, on ati website, for linux

ati_driver_installer-8-10-x86.x86_64.run

---

### Post by Izek on 2008-11-12
> **Rgrmartins said:**
> well i used the one for my graphics card, on ati website, for linux

ati_driver_installer-8-10-x86.x86_64.run

What version of Ubuntu are you running?

---

### Post by Rgrmartins on 2008-11-12
> **izek said:**
> what version of ubuntu are you running?
8.04

---

### Post by dizzy1kenobi on 2008-11-12
Are you using the 64 or 32 bit version of handy?

---

### Post by Rgrmartins on 2008-11-12
> **dizzy1kenobi said:**
> are you using the 64 or 32 bit version of handy?

32

---

### Post by dizzy1kenobi on 2008-11-12
Where did you install compiz from?

---

### Post by haylun98 on 2008-11-12
I had this problem once. I found that the ATI driver installer didn't activate the 3d acceleration driver. You can do it yourself
1. login in Gnome failsafe
2. System > Admin > Hardware drivers
3. Activate and reboot.

Good Luck Rgrmartins

---

### Post by Rgrmartins on 2008-11-12
~$ sudo apt-get install compiz compiz-plugins compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-main python-compizconfig

---

### Post by Rgrmartins on 2008-11-12
> **haylun98 said:**
> I had this problem once. I found that the ATI driver installer didn't activate the 3d acceleration driver. You can do it yourself
1. login in Gnome failsafe
2. System > Admin > Hardware drivers
3. Activate and reboot.

Good Luck Rgrmartins

donne that a few times allready it didnt work, when i reboot its just boot on the normal ubuntu, i have to use the recovery thing

thanks

---

### Post by dizzy1kenobi on 2008-11-12
> **haylun98 said:**
> I had this problem once. I found that the ATI driver installer didn't activate the 3d acceleration driver. You can do it yourself
1. login in Gnome failsafe
2. System > Admin > Hardware drivers
3. Activate and reboot.

Good Luck Rgrmartins

That's right, did you click the driver to "in use"?
Then I think it asked me to upgrade something. I answered yes.
Look at the top of the screen next to the bars is there a big star?

---

### Post by Rgrmartins on 2008-11-12
> **dizzy1kenobi said:**
> That's right, did you click the driver to "in use"?
Then I think it asked me to upgrade something. I answered yes.
Look at the top of the screen next to the bars is there a big star?

nope no star, like i said, it wont strat up :s just stays all black, with no letters in it

edit:managed to start it up, it started with a res of 800x600 unchangable


should i try to run compiz?

---

### Post by dizzy1kenobi on 2008-11-12
You mean your not using that computer right now?

---

### Post by Rgrmartins on 2008-11-12
> **dizzy1kenobi said:**
> You mean your not using that computer right now?

talking on my desktop, problem is on my laptop

---

### Post by Izek on 2008-11-12
If you have libxi6 installed, it may be the problem. The ATI Installer says that libxi6 is not satisfiable. However, libxi6 is required in hardy apparently.

---

### Post by Rgrmartins on 2008-11-12
> **Izek said:**
> If you have libxi6 installed, it may be the problem. The ATI Installer says that libxi6 is not satisfiable. However, libxi6 is required in hardy apparently.

yeah i have that, so what should i do?

---

### Post by Rgrmartins on 2008-11-12
> **Izek said:**
> If you have libxi6 installed, it may be the problem. The ATI Installer says that libxi6 is not satisfiable. However, libxi6 is required in hardy apparently.

well i unistalled the drivers and everything was allright, but when i run compiz i dont get bars from any window.

so i did this $ sudo gedit /etc/X11/xorg.conf

Section "Device"
(...)
Option "XAANoOffscreenPixmaps" "true"
EndSection


didnt worked

---

