---
title: "HOWTO: make all sounds comes from USB headset !"
date: 2008-10-21
forum: Hardware
---

### Post by SiN_AmoR on 2008-10-21
hi guys..

for all who have USB headset (mine is Logitech) and having problems making some sounds, like Adobe Flash, comes from the USB headset. This Thread is what you are looking for :guitar:.

first of all, this HOWTO is tested on Ubuntu 8.04 [Hardy] only !
and these are the list of programs that didn't work with the USB headset:
1) Adobe Flash Player.
2) Kaffiene Multimedia Player.
3) Amarok Music Player.
4) VLC media player.
5) Audacity Sound Editor.
6) Elisa Media Center.

while when setting "USB Audio" in "System -> Preferences -> Sound", only Rhythmbox and Totem worked well with the USB headset !

then, I found the solution that makes "ALL" sounds come from the USB headset \\:D/ :

_**First Step:**_
write this in the terminal:
```
sudo apt-get install asoundconf-gtk
```

it'll make a new menu item at: "System -> Preferences -> Default Sound Card", click it..
then choose "Headset" from the menu..

**_Second Step:_**
go to "System -> Preferences -> Sounds".
and set the first 2 to "Auto detect", and the last 2 to "USB Audio"..

you are done ..
Enjoy your headset .. :guitar:

---

### Post by rakris on 2008-10-21
cool. Thanks. 

In my lappy i get sound both in built-in speakers and external speakers. If i plug out and plug in, then sound comes only in external speakers.

May be i should check this method first once i get home.

---

### Post by Modax42 on 2008-10-22
Thank you. USB headset works now, but there's no volume control.  The headset seems to have only one volume level, and its very very loud.  With some things you solve one problem only to uncover a new one.

---

### Post by wonko on 2008-10-22
Asoundconf-gtk solved (at least partially) [my problem in kde]("http://ubuntuforums.org/showthread.php?t=954589") too. Tanks!

---

