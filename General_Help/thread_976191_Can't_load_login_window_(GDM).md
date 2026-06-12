---
title: "Can't load login window (GDM)"
date: 2008-11-09
forum: General Help
---

### Post by mardangga on 2008-11-09
Hii everyone.....

I got a problem with my ubuntu 8.10.
My ubuntu can't load the login window (GDM).
It's happen after I change the GTK theme with Mac4lin and
add two more item on start up item (start compiz icon and avant
window navigator). 
After I logout, My ubuntu stack can't load the login window.
But it's not 'hang'. It's like loading for something......
Everyone.....
Please help me to fix my problem. 
Thx.......

NB: Sorry 4 my poor English

---

### Post by Peter09 on 2008-11-09
Try rebooting in recovery mode. At the menu select the command prompt.

From the command prompt type

```
startx
```

this should give you a GUI, but for root. If it works you may be able to see whats happened. You could try logging out at the commend prompt. This will give you a textual login. 

Try that as your normal user and the type startx.

---

### Post by tee4cute on 2009-01-06
I've the same problem. I installed "usplash-theme-tangerine" and change the login window to another that's not ubuntu's default. Then I restarted the system and the login window didn't appers. As "mardangga" met, It seems loading for something ...

I'm running on ubuntu 8.04.

I tried to use ctrl+alt+F2 to login by command prompt and switch back to GUI by ctrl+alt+F7 but it doesn't work!!!

I've followed the "Peter09"'s suggestion by running "startx" in recovery mode. I can login by default ubuntu login window in this way. But I can't switch the login window back to default, it says something about "GDM gui doesn't load (I'm not sure)".

Anyone can help me plz!!!

(I think that cant I change the Login Window & Usplash screen back to ubuntu's default by the command line or system config file?)

Thank you!!

---

### Post by brdlvelixir on 2009-01-07
I was having this same problem after installing the "Nubuntu" gdm login themes ([http://gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883](http://gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883)) on ubuntu 8.10 intrepid. Here's how i fixed it:

when the system is sitting there trying to load the login window, hit alt+F2, login with command line. then:

---------------------------------------
cd /usr/share/gdm/themes
ls
sudo rm -rf Problematic_Theme_Folder
exit
---------------------------------------

Now you should have a functional login window come up.


If you try to change your login window again and it keeps going back to the defualt one, open terminal and type:

gksudo gedit /etc/gdm/gdm.conf

hit ctrl+f, search for AllowGtkThemeChange=
make sure it is uncommented and =true

Save it and you should be fine.

---

### Post by tee4cute on 2009-01-07
As "brdlvelixir" suggests :

----------------------------------------------------------------
If you try to change your login window again and it keeps going back to the defualt one, open terminal and type:

gksudo gedit /etc/gdm/gdm.conf

hit ctrl+f, search for AllowGtkThemeChange=
make sure it is uncommented and =true

Save it and you should be fine.
----------------------------------------------------------------

It works!!. I don't need to remove the installed themes just uncomment "AllowGtkThemeChange=" and it works!. Thank you for your reply !!!!

---

