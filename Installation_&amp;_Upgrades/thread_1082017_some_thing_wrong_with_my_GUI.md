---
title: "some thing wrong with my GUI"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by gkraju on 2009-02-27
hi i have installed Ubuntu 8.04(Wubi)
my system hanged (not even keyboard or mouse worked)
so i pressed restart button, at that time update manager was installing some thing
after restart my system GUI changed i checked the Appearance it shows the same properties as before
1)Taskbar is not visible for anything
2)Theme has become grey color
3)All icons have changed
4)when i want to shutdown it comes to the login window there only i can shutdown or restart computer
help me i am new to ubuntu
thanks in advance

---

### Post by gkraju on 2009-02-27
this is my screen shot of my system
[IMG]http://i40.tinypic.com/34dmmnk.png[/IMG]
as you can see the setting has become like windows 98
[IMG]http://i44.tinypic.com/2nichp5.png[/IMG]
the theme is Human but it is showing some theme

---

### Post by abn91c on 2009-02-27
just to make sure go to terminal and do```
sudo dpkg --configure -a
``` followed by```
sudo apt-get update
sudo apt-get upgrade
``` then log out( ctrl+alt+backspace) and restart the xserver(alt+e)

---

### Post by gkraju on 2009-02-27
> **abn91c said:**
> just to make sure go to terminal and do```
sudo dpkg --configure -a
``` followed by```
sudo apt-get update
sudo apt-get upgrade
``` then log out( ctrl+alt+backspace) and restart the xserver(alt+e)

it has not worked problems continue
and also i now noted the music while logging in is also not playing 
but login page is same as before does any one know what could have happened to my system
please help

---

