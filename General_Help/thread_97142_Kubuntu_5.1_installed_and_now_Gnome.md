---
title: "Kubuntu 5.1 installed and now Gnome ?"
date: 2005-11-30
forum: General Help
---

### Post by infoseeker on 2005-11-30
I downloaded Kubuntu Breezy 5.1 and installed it and I am extremely impressed with it ;) What I would like to do now is install Gnome. Are all the required files on the Kubuntu CD and will the Kubuntu install remain intact as it is and can I swop (?) between one and the other? Thx.

---

### Post by Robgould on 2005-11-30
use synaptic, install gnome desktop.....then you will have gnome and kde.
 
When you log in, on the screen where you enter your user name, change your session to kde or gnome, whichever you want for that session.  
 
You don't have to install gnome as you can run all gnome apps from kde or vice versa, but if you want to learn and try gnome go for it. 
 
Glad you like kubuntu.  Welcome aboard!

---

### Post by Xian on 2005-11-30
$ sudo apt-get install ubuntu-desktop

---

### Post by jasay on 2005-11-30
From what I understand, the gnome files are not on the kubuntu cd.  However, you can getg them easily if you have a (relatively) fast internet connection.  Goto System > Administration > Synaptic Package manager.  Then search for ubuntu-desktop.  Click in the box > mark for install > hit apply.  A quicker way to do the same thing is to open a terminal and type (copy/paste) ```
sudo apt-get install ubuntu-desktop
```  Either way, you now have both gnome and kde versions of ubuntu.  You will have to log out of one to get into the other.  Just click on sessions? on the log in and select which desktop environment you want to run.  The only porblem I know of is that the nice short menus get pretty cluttered since they will have programs from both KDE and gnome.

Edit:
Haha. Slow typer.

---

### Post by infoseeker on 2005-11-30
>  sudo apt-get install ubuntu-desktop Password: Reading package lists... Done Building dependency tree... Done E: Couldn't find package ubuntu-desktop  Seems as if Ubuntu / Gnome is not included on the CD :(

Time to get my internet connection up and running ;)

---

### Post by Snipersnest on 2005-11-30
[quote=jasay]From what I understand, the gnome files are not on the kubuntu cd. However, you can getg them easily if you have a (relatively) fast internet connection. Goto System > Administration > Synaptic Package manager. Then search for ubuntu-desktop. Click in the box > mark for install > hit apply. A quicker way to do the same thing is to open a terminal and type (copy/paste) ```
sudo apt-get install ubuntu-desktop
```[/quote]

I'm guessing this will work for both KDE and Gnome? If I'm wanting to add KDE to my Gnome or vice versa?  lol please say yes...I already let it start downloading 151 things...lol

---

### Post by Xian on 2005-11-30
[QUOTE=Snipersnest]I'm guessing this will work for both KDE and Gnome? If I'm wanting to add KDE to my Gnome or vice versa?  lol please say yes...I already let it start downloading 151 things...lol[/QUOTE]

There are basically two set's of meta-pkgs for KDE & Gnome.
With Ubuntu it is the one you posted above.

For Kubuntu (KDE) it is:

$ sudo apt-get install kubuntu-desktop

---

### Post by Snipersnest on 2005-12-01
lol ok so I'll have the option when I'm at the login screen to pick my desktop right?

---

### Post by infoseeker on 2005-12-01
Connected to the net and issued.....
> sudo apt-get install ubuntu-desktop
and am now proud to say I am typing this from Gnome and Mozilla Firefox :p 
Took about 100MB of downloading, and later some more for updates, and it looks good.

Thanks for the advice.

---

