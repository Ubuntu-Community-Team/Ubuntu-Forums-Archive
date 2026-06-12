---
title: "Shortcuts On ubuntu"
date: 2008-10-30
forum: General Help
---

### Post by markomk on 2008-10-30
Hi i'm new user and i need a little help

i used Windows XP until few months when i install openSuse,but i had some problems with openSuse and i try Ubuntu,i think it was great choice,but when i install some program i can only run from Terminal :S(some program had a shortcut for ex. Skype)where i can find a shortcut from the installed programs? 

tnx:)

---

### Post by Idefix82 on 2008-10-30
Most graphical programs that you install through Synaptic will automatically add a shortcut in the main menu. Otherwise you can create your custom launchers by right clicking on the panel on the top and choosing "Add", then something like "Custom launcher". Which programs are you talking about in particular?

---

### Post by Coreigh on 2008-10-30
If the programs are installed from supported packages with Add/Remove or Synaptic (or manually in the terminal) then a launcher will be placed in the Application Menu (upper left corner of screen by default) 

If the launcher is in the Application Menu and you want it on the Desktop or task bar you can right-click on it and choose add to Desktop or Panel.

If it is a custom installation, 3rd party software or otherwise unofficial/unsupported you will have to create a launcher. Right-click on the Desktop and choose create launcher. You can also add to or edit the Application menu by right-clicking on the menu and choosing "edit menus."

[http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html")

I hope this helps.

---

### Post by markomk on 2008-10-30
I try to install with apt-get and some tar.gz programs

---

### Post by Druke on 2008-10-30
what programs are we talking about? if you install from a compressed folder, you have to do alot fo that yourself. If you install from a .deb or from synaptic/add-remove then its all automatic.

ON the other hand.. you don't mean desktop short cuts do you? If so, find the app in your applications menu, right click, and "add this launcher to desktop".

---

### Post by bodhi.zazen on 2008-10-30
Sometimes after you install a program you need to log out and back in to update your menu.

---

### Post by markomk on 2008-10-30
> **Druke said:**
> what programs are we talking about? if you install from a compressed folder, you have to do alot fo that yourself. If you install from a .deb or from synaptic/add-remove then its all automatic.

ON the other hand.. you don't mean desktop short cuts do you? If so, find the app in your applications menu, right click, and "add this launcher to desktop".

No no Desktop short cuts from applications menu, for ex. few days ago i try to install aMSN it was compressed,i extracted and try to install from therminal
./configure
make....
...
when i finish with instalation i can't find the aMSN application  :S

---

### Post by PsychedelicReaction on 2008-10-30
mmh are you sure that the make and make install went fine, without errors? try to type amsn in the console and see what happens, if it says command not found you probably missed some dependencies during the making process. however amsn, like the big part of the most used programs, are avaiable in some repository. just google it before trying to make it by yourself, it's easier than compiling ;)

---

### Post by Druke on 2008-10-30
> **markomk said:**
> No no Desktop short cuts from applications menu, for ex. few days ago i try to install aMSN it was compressed,i extracted and try to install from therminal
./configure
make....
...
when i finish with instalation i can't find the aMSN application  :S

ok I understand now.

so you start amsn by typing amsn into a terminal, but you don't like that (understandably!)

there is a better way to do this whole thing, but first I'll teach you how to do it this way (it's a good learning experience.


ok... to get a shortcut ... let's say in the applications menu. 
[LIST=1]
[*]right click on applications
[*]select edit menus
[*]select a category on the left (in the case of amsn, I'd file it under Internet)
[*]select new item, from the right
[*]a window called ,create launcher, appears
[*]insert desired name in the field (in th case of amsn, I'd call it AMsn)
[*]in command, put the termianl command for the app (in this case "amsn")
[*]hit ok, and your done!
[/LIST]


ok now the asy way to do this all automatically.

Via Add Remove (recommended)
[LIST=1]
[*]click "Applications"
[*]select "Add remove" at the bottom of the list
[*]in the box on the top right, type "amsn"
[*]hit the check box beside amsn in the list
[*]then hit apply changes on the bottom right
[/LIST]

via terminal (faster, but requires a terminal)
paste this into a terminal
```
sudo apt-get install amsn
```
and your done.

---

