---
title: "Wine question"
date: 2008-08-29
forum: General Help
---

### Post by ^^rac on 2008-08-29
Hi guys!

1) I installed Wine, then removed it, to do a Fresh install.....

Its working great, but i accedentially, removed the "Wine" menu from the program list.......

Its easy to access the Windows apps from there....

I tried to get it back, but cant. Can someone assist me to get this back in the program list?

2) Is there a size limit to what one can install in Wine, i mean, can i install 10 GB's worth of apps on the virtual C drive?

Thanks guys!

Cheers from Africa!

---

### Post by frup on 2008-08-29
If wine is in fact installed, you may wish to check the main menu application in system > preferences.

Did you install wine from winehq or from ubuntu's repositories?

---

### Post by EnGorDiaz on 2008-08-29
> **^^rac said:**
> Hi guys!

1) I installed Wine, then removed it, to do a Fresh install.....

Its working great, but i accedentially, removed the "Wine" menu from the program list.......

Its easy to access the Windows apps from there....

I tried to get it back, but cant. Can someone assist me to get this back in the program list?

2) Is there a size limit to what one can install in Wine, i mean, can i install 10 GB's worth of apps on the virtual C drive?

Thanks guys!

Cheers from Africa!

ok here what you need to do

first goto your main menu right click then youll see a thing called edit menus 

second click on it and then youll see a tab called new menu then make a Wine menu press enter

3rdly you have to get your shortcuts back so now

click new item then put in the 

name:Browse C:\ Drive
command:xdg-open ~/.wine/drive_c

then again

name:configure wine
command:winecfg

name:uninstall wine software
command:uninstaller

all done except the icons but dont worry about them you got all your stuff back so click browse c drive get all your then pinpoint each individual program exe in your /home/urusername/.wine/drive_c/Program Files

and create shortcuts for them on your desktop and your done :)

---

### Post by ^^rac on 2008-08-29
> **frup said:**
> If wine is in fact installed, you may wish to check the main menu application in system > preferences.

Did you install wine from winehq or from ubuntu's repositories?

Hi there....

I installed it from ubuntu's repositories.
The Menu was there, i just disabled it in the menu settings, but now, i cant get it again.....

Hehehe, crazy!

---

### Post by EnGorDiaz on 2008-08-29
hope your happy with that and the smiley that goes like this :mad: the command is again xdg-open ~/.wine/drive_c in the browse c drive option

---

### Post by Crafty Kisses on 2008-08-29
Try running Wine in Terminal you get anything?

---

### Post by ^^rac on 2008-08-29
> **EnGorDiaz said:**
> hope your happy with that and the smiley that goes like this :mad: the command is again xdg-open ~/.wine/drive_c in the browse c drive option


Thanks alot guys!
Ill try it tonight, and let yous know!

Also, is there any limit as to how much progs i install on the virtual C: drive??

Thanks alot!

---

### Post by Crafty Kisses on 2008-08-29
> **^^rac said:**
> Thanks alot guys!
Ill try it tonight, and let yous know!

Also, is there any limit as to how much progs i install on the virtual C: drive??

Thanks alot!

I don't think so.

---

### Post by EnGorDiaz on 2008-08-29
> **^^rac said:**
> Thanks alot guys!
Ill try it tonight, and let yous know!

Also, is there any limit as to how much progs i install on the virtual C: drive??

Thanks alot!

there isnt unless you set it

---

### Post by EnGorDiaz on 2008-08-29
> **Codename said:**
> Try running Wine in Terminal you get anything?

correction type wine in the run prompt

---

### Post by Crafty Kisses on 2008-08-29
> **EnGorDiaz said:**
> correction type wine in the run prompt
Well I was doing it with correct punctuation, but yeah if you want to correct me go ahead.

---

### Post by EnGorDiaz on 2008-08-29
> **Codename said:**
> Well I was doing it with correct punctuation, but yeah if you want to correct me go ahead.

it doesnt work anyway i tryed it its best to use my instructions for the menus it gets them all back up

---

