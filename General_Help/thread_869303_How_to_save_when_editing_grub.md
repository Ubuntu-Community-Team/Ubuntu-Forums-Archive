---
title: "How to save when editing grub"
date: 2008-07-24
forum: General Help
---

### Post by wbutchart on 2008-07-24
Hi im having to make changes to the grub thing via root command to fix a blank screen on start up.  When i make the changes to menu.lst i dont know how to save them.  Which button or code saves it when i have made the changes.

At the moment the only way i know to get out of the edit screen is to switch the computer off which erases the changes.

Thanks.

---

### Post by Vivaldi Gloria on 2008-07-24
> **wbutchart said:**
> Hi im having to make changes to the grub thing via root command to fix a blank screen on start up.  When i make the changes to menu.lst i dont know how to save them.  Which button or code saves it when i have made the changes.

At the moment the only way i know to get out of the edit screen is to switch the computer off which erases the changes.

Thanks.

Make the changes, press b to boot your computer with those changes. (Actually the edit menu writes the options below). This will boot with those changes but to make them permanent you need to edit menu.lst. Press ALT+F2 and start

```
gksudo gedit /boot/grub/menu.lst
```

and make the changes you want again. Now save.

---

### Post by wbutchart on 2008-07-24
> **Vivaldi Gloria said:**
> Make the changes, press b to boot your computer with those changes. (Actually the edit menu writes the options below). This will boot with those changes but to make them permanent you need to edit menu.lst. Press ALT+F2 and start

```
gksudo gedit /boot/grub/menu.lst
```

and make the changes you want again. Now save.
Thats where im at you said make the changes then save but HOW do i save, when im editing menu.lst there is NO save option.

---

### Post by Oldsoldier2003 on 2008-07-24
> **wbutchart said:**
> Thats where im at you said make the changes then save but HOW do i save, when im editing menu.lst there is NO save option.

as said above there is no save option in grub. you'll need to edit /boot/grub/menu.lst and save the changes to the file. In order to save you'll need to be running your text editor with superuser privs. 
```

sudo nano /boot/grub/menu.lst
```

---

### Post by wbutchart on 2008-07-24
> **Oldsoldier2003 said:**
> as said above there is no save option in grub. you'll need to edit /boot/grub/menu.lst and save the changes to the file. In order to save you'll need to be running your text editor with superuser privs. 
```

sudo nano /boot/grub/menu.lst
```
I cant do that because ubuntu loads wiith a blank screen.  Im having to try and edit with the code sudo vi /boot/grub/menu.lst in root command in recovery mode.  There must be some way to save it otherwise whats the point of the function?.  I cannot use ubuntu after the loading screen its just a blakn screen i need to edit the grub thing.

---

### Post by tonez2600 on 2008-07-24
```
sudo nano /boot/grub/menu.lst
```

after that you will be in text editor (nano) from there write your changes, and then press

CTRL+O

to save, and then 

CTRL+X

to exit nano. hope this can be of help to you.

---

### Post by oneporter on 2008-07-24
Use nano instead of vi (only because I've never used vi and don't know the commands).   In the recovery console just type "nano /boot/grub/menu.lst".  When you're done editing, press ctrl + x, it will ask you if you want to save and where. Then you can restart with "shutdown -r now".

---

### Post by Dylock on 2008-07-24
:w should save the file in vi
If you want to save and close vi then use :wq

---

### Post by tonez2600 on 2008-07-24
> **wbutchart said:**
> I cant do that because ubuntu loads wiith a blank screen.  Im having to try and edit with the code sudo vi /boot/grub/menu.lst in root command in recovery mode.  There must be some way to save it otherwise whats the point of the function?.  I cannot use ubuntu after the loading screen its just a blakn screen i need to edit the grub thing.

try writing your changes and then use :wq to save, seeing that you are useing vi. :wq is the save and quit command for vi, hope that helps.

---

